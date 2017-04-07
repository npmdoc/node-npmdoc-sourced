# api documentation for  [sourced (v0.1.4)](https://github.com/mateodelnorte/sourced#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-sourced.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-sourced) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-sourced.svg)](https://travis-ci.org/npmdoc/node-npmdoc-sourced)
#### Tiny framework for building models with the event sourcing  pattern (events and snapshots).

[![NPM](https://nodei.co/npm/sourced.png?downloads=true)](https://www.npmjs.com/package/sourced)

[![apidoc](https://npmdoc.github.io/node-npmdoc-sourced/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-sourced_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-sourced/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-sourced/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-sourced/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "mattwalters5@gmail.com"
    },
    "bugs": {
        "url": "https://github.com/mateodelnorte/sourced/issues"
    },
    "dependencies": {
        "debug": "~0.7.2",
        "lodash": "^2.4.1"
    },
    "description": "Tiny framework for building models with the event sourcing  pattern (events and snapshots).",
    "devDependencies": {
        "mocha": "~1.11.0",
        "should": "~1.2.2"
    },
    "directories": {},
    "dist": {
        "shasum": "d2fe271ad1f0b8b99d150332deba161be85d98ab",
        "tarball": "https://registry.npmjs.org/sourced/-/sourced-0.1.4.tgz"
    },
    "gitHead": "d29315b89f476ed8d5c44ead515e03fd15c90139",
    "homepage": "https://github.com/mateodelnorte/sourced#readme",
    "license": "BSD",
    "main": "index.js",
    "maintainers": [
        {
            "name": "mateodelnorte",
            "email": "mattwalters5@gmail.com"
        }
    ],
    "name": "sourced",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+ssh://git@github.com/mateodelnorte/sourced.git"
    },
    "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
    },
    "version": "0.1.4"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module sourced](#apidoc.module.sourced)
1.  [function <span class="apidocSignatureSpan">sourced.</span>Entity ()](#apidoc.element.sourced.Entity)
1.  [function <span class="apidocSignatureSpan">sourced.</span>Value (obj)](#apidoc.element.sourced.Value)
1.  object <span class="apidocSignatureSpan">sourced.</span>Entity.prototype

#### [module sourced.Entity](#apidoc.module.sourced.Entity)
1.  [function <span class="apidocSignatureSpan">sourced.</span>Entity ()](#apidoc.element.sourced.Entity.Entity)
1.  [function <span class="apidocSignatureSpan">sourced.Entity.</span>digestMethod (type, fn)](#apidoc.element.sourced.Entity.digestMethod)
1.  [function <span class="apidocSignatureSpan">sourced.Entity.</span>mergeProperty (type, name, fn)](#apidoc.element.sourced.Entity.mergeProperty)
1.  [function <span class="apidocSignatureSpan">sourced.Entity.</span>super_ ()](#apidoc.element.sourced.Entity.super_)

#### [module sourced.Entity.prototype](#apidoc.module.sourced.Entity.prototype)
1.  [function <span class="apidocSignatureSpan">sourced.Entity.prototype.</span>digest (method, data)](#apidoc.element.sourced.Entity.prototype.digest)
1.  [function <span class="apidocSignatureSpan">sourced.Entity.prototype.</span>emit ()](#apidoc.element.sourced.Entity.prototype.emit)
1.  [function <span class="apidocSignatureSpan">sourced.Entity.prototype.</span>enqueue ()](#apidoc.element.sourced.Entity.prototype.enqueue)
1.  [function <span class="apidocSignatureSpan">sourced.Entity.prototype.</span>merge (snapshot)](#apidoc.element.sourced.Entity.prototype.merge)
1.  [function <span class="apidocSignatureSpan">sourced.Entity.prototype.</span>mergeProperty (name, value)](#apidoc.element.sourced.Entity.prototype.mergeProperty)
1.  [function <span class="apidocSignatureSpan">sourced.Entity.prototype.</span>replay (events)](#apidoc.element.sourced.Entity.prototype.replay)
1.  [function <span class="apidocSignatureSpan">sourced.Entity.prototype.</span>snapshot ()](#apidoc.element.sourced.Entity.prototype.snapshot)
1.  [function <span class="apidocSignatureSpan">sourced.Entity.prototype.</span>trimSnapshot (snapshot)](#apidoc.element.sourced.Entity.prototype.trimSnapshot)



# <a name="apidoc.module.sourced"></a>[module sourced](#apidoc.module.sourced)

#### <a name="apidoc.element.sourced.Entity"></a>[function <span class="apidocSignatureSpan">sourced.</span>Entity ()](#apidoc.element.sourced.Entity)
- description and source-code
```javascript
function Entity() {

<span class="apidocCodeCommentSpan">  /**
   * [Description]
   *
   * @member {Array} eventsToEmit
   * @todo discuss the use of this so it can be documented better.
   */
</span>  this.eventsToEmit = [];

  /**
   * [Description]
   *
   * @member {Array} newEvents
   * @todo discuss the use of this so it can be documented better.
   */
  this.newEvents = [];

  /**
   * Boolean to prevent emit, enqueue and digest from running during replay.
   *
   * @member {Boolean} replaying
   */
  this.replaying = false;

  /**
   * Holds the version of the latest snapshot for the entity.
   *
   * @member {Number} snapshotVersion
   */
  this.snapshotVersion = 0;

  /**
   * Holds the event's timestamp in the entity.
   *
   * @member {Number} timestamp
   */
  this.timestamp = Date.now();

  /**
   * Holds the current version of the entity.
   *
   * @member {Number} version
   */
  this.version = 0;

  events.EventEmitter.call(this);
  var args = Array.prototype.slice.call(arguments);

  /**
   * If one argument is passed, asume it's a snapshot and merge it.
   *
   * @todo This should probably be changed. What if it's not a snapshot/object?
   */
  if (args[0]){
    var snapshot = args[0];
    this.merge(snapshot);
  }

  /**
   * If two arguments are passed, asume the second is an array of events and
   * replay them.
   *
   * @todo This should probably be changed. What if it's not an array?
   */
  if (args[1]){
    var evnts = args[1];
    this.replay(evnts);
  }
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.sourced.Value"></a>[function <span class="apidocSignatureSpan">sourced.</span>Value (obj)](#apidoc.element.sourced.Value)
- description and source-code
```javascript
Value = function (obj) {
  return Object.freeze(obj);
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.sourced.Entity"></a>[module sourced.Entity](#apidoc.module.sourced.Entity)

#### <a name="apidoc.element.sourced.Entity.Entity"></a>[function <span class="apidocSignatureSpan">sourced.</span>Entity ()](#apidoc.element.sourced.Entity.Entity)
- description and source-code
```javascript
function Entity() {

<span class="apidocCodeCommentSpan">  /**
   * [Description]
   *
   * @member {Array} eventsToEmit
   * @todo discuss the use of this so it can be documented better.
   */
</span>  this.eventsToEmit = [];

  /**
   * [Description]
   *
   * @member {Array} newEvents
   * @todo discuss the use of this so it can be documented better.
   */
  this.newEvents = [];

  /**
   * Boolean to prevent emit, enqueue and digest from running during replay.
   *
   * @member {Boolean} replaying
   */
  this.replaying = false;

  /**
   * Holds the version of the latest snapshot for the entity.
   *
   * @member {Number} snapshotVersion
   */
  this.snapshotVersion = 0;

  /**
   * Holds the event's timestamp in the entity.
   *
   * @member {Number} timestamp
   */
  this.timestamp = Date.now();

  /**
   * Holds the current version of the entity.
   *
   * @member {Number} version
   */
  this.version = 0;

  events.EventEmitter.call(this);
  var args = Array.prototype.slice.call(arguments);

  /**
   * If one argument is passed, asume it's a snapshot and merge it.
   *
   * @todo This should probably be changed. What if it's not a snapshot/object?
   */
  if (args[0]){
    var snapshot = args[0];
    this.merge(snapshot);
  }

  /**
   * If two arguments are passed, asume the second is an array of events and
   * replay them.
   *
   * @todo This should probably be changed. What if it's not an array?
   */
  if (args[1]){
    var evnts = args[1];
    this.replay(evnts);
  }
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.sourced.Entity.digestMethod"></a>[function <span class="apidocSignatureSpan">sourced.Entity.</span>digestMethod (type, fn)](#apidoc.element.sourced.Entity.digestMethod)
- description and source-code
```javascript
digestMethod = function (type, fn) {
  if ( ! type) throw new EntityError('type is required for digest method definitions');
  if ( ! fn) throw new EntityError('a function is required for digest method definitions');
  if ( ! fn.name) throw new EntityError('Anonmyous functions are not allowed in digest method definitions. Please provide a function
 name');
  type.prototype[fn.name] = function () {
    var digestArgs = Array.prototype.slice.call(arguments);
    digestArgs.unshift(fn.name);
    Entity.prototype.digest.apply(this, digestArgs);

    var methodArgs = Array.prototype.slice.call(arguments);
    return fn.apply(this, methodArgs);
  };
}
```
- example usage
```shell
...
        * [.digest(method, data)](#Entity+digest)
        * [.merge(snapshot)](#Entity+merge)
        * [.mergeProperty(name, value)](#Entity+mergeProperty)
        * [.replay(events)](#Entity+replay)
        * [.snapshot()](#Entity+snapshot) ⇒ <code>Object</code>
        * [.trimSnapshot(snapshot)](#Entity+trimSnapshot)
    * _static_
        * [.digestMethod(type, fn)](#Entity.digestMethod)
        * [.mergeProperty(type, name, fn)](#Entity.mergeProperty)

<a name="new_Entity_new"></a>

### new Entity([snapshot], [events])
Creates an event-sourced Entity.
...
```

#### <a name="apidoc.element.sourced.Entity.mergeProperty"></a>[function <span class="apidocSignatureSpan">sourced.Entity.</span>mergeProperty (type, name, fn)](#apidoc.element.sourced.Entity.mergeProperty)
- description and source-code
```javascript
mergeProperty = function (type, name, fn) {
  if ( ! mergeProperties.has(type.name)) mergeProperties.set(type.name, new Map());
  mergeProperties.get(type.name).set(name, fn);
}
```
- example usage
```shell
...
* [Entity](#Entity)
* [new Entity([snapshot], [events])](#new_Entity_new)
* _instance_
    * [.emit()](#Entity+emit)
    * [.enqueue()](#Entity+enqueue)
    * [.digest(method, data)](#Entity+digest)
    * [.merge(snapshot)](#Entity+merge)
    * [.mergeProperty(name, value)](#Entity+mergeProperty)
    * [.replay(events)](#Entity+replay)
    * [.snapshot()](#Entity+snapshot) ⇒ <code>Object</code>
    * [.trimSnapshot(snapshot)](#Entity+trimSnapshot)
* _static_
    * [.digestMethod(type, fn)](#Entity.digestMethod)
    * [.mergeProperty(type, name, fn)](#Entity.mergeProperty)
...
```

#### <a name="apidoc.element.sourced.Entity.super_"></a>[function <span class="apidocSignatureSpan">sourced.Entity.</span>super_ ()](#apidoc.element.sourced.Entity.super_)
- description and source-code
```javascript
function EventEmitter() {
  EventEmitter.init.call(this);
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.sourced.Entity.prototype"></a>[module sourced.Entity.prototype](#apidoc.module.sourced.Entity.prototype)

#### <a name="apidoc.element.sourced.Entity.prototype.digest"></a>[function <span class="apidocSignatureSpan">sourced.Entity.prototype.</span>digest (method, data)](#apidoc.element.sourced.Entity.prototype.digest)
- description and source-code
```javascript
function digest(method, data) {
  if( ! this.replaying) {
    this.timestamp = Date.now();
    this.version = this.version + 1;
    log(util.format('digesting event \'%s\' w/ data %j', method, data));
    this.newEvents.push({
      method: method,
      data: data,
      timestamp: this.timestamp,
      version: this.version
    });
  }
}
```
- example usage
```shell
...
**License**: MIT

* [Entity](#Entity)
* [new Entity([snapshot], [events])](#new_Entity_new)
* _instance_
    * [.emit()](#Entity+emit)
    * [.enqueue()](#Entity+enqueue)
    * [.digest(method, data)](#Entity+digest)
    * [.merge(snapshot)](#Entity+merge)
    * [.mergeProperty(name, value)](#Entity+mergeProperty)
    * [.replay(events)](#Entity+replay)
    * [.snapshot()](#Entity+snapshot) ⇒ <code>Object</code>
    * [.trimSnapshot(snapshot)](#Entity+trimSnapshot)
* _static_
    * [.digestMethod(type, fn)](#Entity.digestMethod)
...
```

#### <a name="apidoc.element.sourced.Entity.prototype.emit"></a>[function <span class="apidocSignatureSpan">sourced.Entity.prototype.</span>emit ()](#apidoc.element.sourced.Entity.prototype.emit)
- description and source-code
```javascript
function emit() {
  if ( ! this.replaying) {
    events.EventEmitter.prototype.emit.apply(this, arguments);
  }
}
```
- example usage
```shell
...
**Kind**: global class
**Requires**: <code>module:events</code>, <code>module:debug</code>, <code>module:util</code>, <code>module:lodash</code>
**License**: MIT

* [Entity](#Entity)
* [new Entity([snapshot], [events])](#new_Entity_new)
* _instance_
    * [.emit()](#Entity+emit)
    * [.enqueue()](#Entity+enqueue)
    * [.digest(method, data)](#Entity+digest)
    * [.merge(snapshot)](#Entity+merge)
    * [.mergeProperty(name, value)](#Entity+mergeProperty)
    * [.replay(events)](#Entity+replay)
    * [.snapshot()](#Entity+snapshot) ⇒ <code>Object</code>
    * [.trimSnapshot(snapshot)](#Entity+trimSnapshot)
...
```

#### <a name="apidoc.element.sourced.Entity.prototype.enqueue"></a>[function <span class="apidocSignatureSpan">sourced.Entity.prototype.</span>enqueue ()](#apidoc.element.sourced.Entity.prototype.enqueue)
- description and source-code
```javascript
function enqueue() {
  if ( ! this.replaying) {
    this.eventsToEmit.push(arguments);
  }
}
```
- example usage
```shell
...
**Requires**: <code>module:events</code>, <code>module:debug</code>, <code>module:util</code>, <code>module:lodash</code>
**License**: MIT

* [Entity](#Entity)
* [new Entity([snapshot], [events])](#new_Entity_new)
* _instance_
    * [.emit()](#Entity+emit)
    * [.enqueue()](#Entity+enqueue)
    * [.digest(method, data)](#Entity+digest)
    * [.merge(snapshot)](#Entity+merge)
    * [.mergeProperty(name, value)](#Entity+mergeProperty)
    * [.replay(events)](#Entity+replay)
    * [.snapshot()](#Entity+snapshot) ⇒ <code>Object</code>
    * [.trimSnapshot(snapshot)](#Entity+trimSnapshot)
* _static_
...
```

#### <a name="apidoc.element.sourced.Entity.prototype.merge"></a>[function <span class="apidocSignatureSpan">sourced.Entity.prototype.</span>merge (snapshot)](#apidoc.element.sourced.Entity.prototype.merge)
- description and source-code
```javascript
function merge(snapshot) {
  log(util.format('merging snapshot %j', snapshot));
  for (var property in snapshot) {
    if (snapshot.hasOwnProperty(property))
      var val = _.cloneDeep(snapshot[property]);
      this.mergeProperty(property, val);
  }
  return this;
}
```
- example usage
```shell
...

* [Entity](#Entity)
* [new Entity([snapshot], [events])](#new_Entity_new)
* _instance_
    * [.emit()](#Entity+emit)
    * [.enqueue()](#Entity+enqueue)
    * [.digest(method, data)](#Entity+digest)
    * [.merge(snapshot)](#Entity+merge)
    * [.mergeProperty(name, value)](#Entity+mergeProperty)
    * [.replay(events)](#Entity+replay)
    * [.snapshot()](#Entity+snapshot) ⇒ <code>Object</code>
    * [.trimSnapshot(snapshot)](#Entity+trimSnapshot)
* _static_
    * [.digestMethod(type, fn)](#Entity.digestMethod)
    * [.mergeProperty(type, name, fn)](#Entity.mergeProperty)
...
```

#### <a name="apidoc.element.sourced.Entity.prototype.mergeProperty"></a>[function <span class="apidocSignatureSpan">sourced.Entity.prototype.</span>mergeProperty (name, value)](#apidoc.element.sourced.Entity.prototype.mergeProperty)
- description and source-code
```javascript
function mergeProperty(name, value) {
  if (mergeProperties.size &&
      mergeProperties.has(this.__proto__.constructor.name) &&
      mergeProperties.get(this.__proto__.constructor.name).has(name) &&
      typeof mergeProperties.get(this.__proto__.constructor.name).get(name) === 'function') {
    return mergeProperties.get(this.__proto__.constructor.name).get(name).call(this, value);
  }
  else if (typeof value === 'object' && typeof this[name] === 'object') _.merge(this[name], value);
  else this[name] = value;
}
```
- example usage
```shell
...
* [Entity](#Entity)
* [new Entity([snapshot], [events])](#new_Entity_new)
* _instance_
    * [.emit()](#Entity+emit)
    * [.enqueue()](#Entity+enqueue)
    * [.digest(method, data)](#Entity+digest)
    * [.merge(snapshot)](#Entity+merge)
    * [.mergeProperty(name, value)](#Entity+mergeProperty)
    * [.replay(events)](#Entity+replay)
    * [.snapshot()](#Entity+snapshot) ⇒ <code>Object</code>
    * [.trimSnapshot(snapshot)](#Entity+trimSnapshot)
* _static_
    * [.digestMethod(type, fn)](#Entity.digestMethod)
    * [.mergeProperty(type, name, fn)](#Entity.mergeProperty)
...
```

#### <a name="apidoc.element.sourced.Entity.prototype.replay"></a>[function <span class="apidocSignatureSpan">sourced.Entity.prototype.</span>replay (events)](#apidoc.element.sourced.Entity.prototype.replay)
- description and source-code
```javascript
function replay(events) {
  var self = this;

  this.replaying = true;

  log(util.format('replaying events %j', events));

  events.forEach(function (event) {
    if (self[event.method]) {
      self[event.method](event.data);
      self.version = event.version;
    } else {
      var classNameRegex = /function (.{1,})\w?\(/,
          className = classNameRegex.exec(self.constructor.toString())[1],
          errorMessage = util.format('method \'%s\' does not exist on model \'%s\'', event.method, className);
      log(errorMessage);
      throw new EntityError(errorMessage);
    }
  });

  this.replaying = false;
}
```
- example usage
```shell
...
    * [new Entity([snapshot], [events])](#new_Entity_new)
    * _instance_
        * [.emit()](#Entity+emit)
        * [.enqueue()](#Entity+enqueue)
        * [.digest(method, data)](#Entity+digest)
        * [.merge(snapshot)](#Entity+merge)
        * [.mergeProperty(name, value)](#Entity+mergeProperty)
        * [.replay(events)](#Entity+replay)
        * [.snapshot()](#Entity+snapshot) ⇒ <code>Object</code>
        * [.trimSnapshot(snapshot)](#Entity+trimSnapshot)
    * _static_
        * [.digestMethod(type, fn)](#Entity.digestMethod)
        * [.mergeProperty(type, name, fn)](#Entity.mergeProperty)

<a name="new_Entity_new"></a>
...
```

#### <a name="apidoc.element.sourced.Entity.prototype.snapshot"></a>[function <span class="apidocSignatureSpan">sourced.Entity.prototype.</span>snapshot ()](#apidoc.element.sourced.Entity.prototype.snapshot)
- description and source-code
```javascript
function snapshot() {
  this.snapshotVersion = this.version;
  var snap = _.cloneDeep(this, true);
  return this.trimSnapshot(snap);
}
```
- example usage
```shell
...
    * _instance_
        * [.emit()](#Entity+emit)
        * [.enqueue()](#Entity+enqueue)
        * [.digest(method, data)](#Entity+digest)
        * [.merge(snapshot)](#Entity+merge)
        * [.mergeProperty(name, value)](#Entity+mergeProperty)
        * [.replay(events)](#Entity+replay)
        * [.snapshot()](#Entity+snapshot) ⇒ <code>Object</code>
        * [.trimSnapshot(snapshot)](#Entity+trimSnapshot)
    * _static_
        * [.digestMethod(type, fn)](#Entity.digestMethod)
        * [.mergeProperty(type, name, fn)](#Entity.mergeProperty)

<a name="new_Entity_new"></a>
...
```

#### <a name="apidoc.element.sourced.Entity.prototype.trimSnapshot"></a>[function <span class="apidocSignatureSpan">sourced.Entity.prototype.</span>trimSnapshot (snapshot)](#apidoc.element.sourced.Entity.prototype.trimSnapshot)
- description and source-code
```javascript
function trimSnapshot(snapshot) {
  delete snapshot.eventsToEmit;
  delete snapshot.newEvents;
  delete snapshot.replaying;
  delete snapshot._events;
  delete snapshot._maxListeners;
  delete snapshot.domain;
  return snapshot;
}
```
- example usage
```shell
...
        * [.emit()](#Entity+emit)
        * [.enqueue()](#Entity+enqueue)
        * [.digest(method, data)](#Entity+digest)
        * [.merge(snapshot)](#Entity+merge)
        * [.mergeProperty(name, value)](#Entity+mergeProperty)
        * [.replay(events)](#Entity+replay)
        * [.snapshot()](#Entity+snapshot) ⇒ <code>Object</code>
        * [.trimSnapshot(snapshot)](#Entity+trimSnapshot)
    * _static_
        * [.digestMethod(type, fn)](#Entity.digestMethod)
        * [.mergeProperty(type, name, fn)](#Entity.mergeProperty)

<a name="new_Entity_new"></a>

### new Entity([snapshot], [events])
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
