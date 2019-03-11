### power-assert
---
https://github.com/power-assert-js/power-assert

```js
'use strict';

const assert = require('assert');

describe('Array', function(){
  let ary;
  beforeEach(() => {
    ary = [1,2,3];
  });
  describe('#indexOf()', () => {
    it('should return index when the value is present', () => {
      const zero = 0, two = 2;
      assert(ary.indexOf(zero) === two);
    });
    it('should return -1 when the value is not present', () => {
      const minusOne = -1, two = 2;
      assert.ok(ary.indexOf(two) === minusOne, 'THIS IS AN ASSERTION MESSAGE');
    });
  });
});

describe('various types', () => {
  let types;
  class Person {
    constructor(name, age) {
      this.name = name;
      this.age = age;
    }
  }
  beforeEach(() => {
    types = [
      'string', 98.6, true, false, null, undefined,
      ['nested', 'array'],
      {object: true},
      NaN, Infinity,
      /^not/,
      new Person('alice', 3)
    ];
  });
  it('demo', () => {
    const index = types.length -1,
      bob = new Person('bob', 5);
    assert(types[index].name === bob.name);
  });
});

var assert = require('power-assert').custominze({
  output: {
    maxDepth: 2
  }
});

var assert = require('power-assert').customize({
  assertion: {
    destructive: false,
    modifyMessageOnRethrow: true,
    saveContextOnRethrow: true,
    patterns: [
      'assert(value, [message])',
      'assert.ok(value, [message])',
      'assert.equal(actual, expected, [message])', 
      'assert.notEqual(actual, expected, [message])',
      'assert.strictEqual(actual, expected, [message])', 
      'assert.notStrictEqual(actual, expected, [message])',
      'assert.deepEqual(actual, expected, [message])',
      'assert.notDeepEqual(actual, expected, [message])',
      'assert.deepStrictEqual(actual, expected, [message])',
      'assert.notDeepStrictEqual(actual, expected, [message])'
    ]
  },
  output: {
    lineDiffThreshold: 5,
    maxDepth: 1,
    anonymous: 'Object',
    circular: '#@Circular#',
    lineSeparator: '\n',
    ambigousEastAsianCharWidth: 2,
    widthOf: (Function to calculate width of string.Please see power-formatter's documentation)
    stringify: (Funciton to stringify any target value. Please see power-assert-formatter's documentation)
    diff: (Funciton to create diff string between two strings. Please see power-assert-formatter's documentation)
    writerClass: (Constructor Function for output writer class. Plsase see power-assert-formatter's documentation)
    renderers: [
      './built-in/file',
      './built-in/assertion',
      './built-in/diagram',
      './built-in/binary-expression'
    ]
  }
});


var q = require('qunitjs');

(function () {
  var empower = require('empower');
    formatter = require('power-assert-formatter'),
    quintTap = require("quint-tap");
  empower(q.assert, formatter(), {destructive: true});
  quintTap(q, require('util').puts, {showSourceOnFailure: false});
  q.config.autorun = false;
})();

q.test('spike', function (assert) {
  assert.ok(true);
  
  var hoge = 'foo';
  var fuga = 'bar';
  assert.ok(hoge === fuga, 'comment');
  
  var piyo = 3;
  assert.ok(fuga === piyo);
  
  var longString = 'very very looooooooong message';
  var anotherLongString = 'yet another looong message';
  assert.ok(longString === anotherLongString);
  
  assert.ok(4 === piyo);
  
  assert.ok(4 !== 4);
  
  var falsyStr = '';
  assert.ok(falsyStr);
  
  var falsyNum = 0;
  assert.ok(falsyNum);
  
  var ary1 = ['foo', 'bar'];
  var ary2 = ['aaa', 'bbb', 'ccc'];
  assert.ok(ary1.length === ary2.length);
  assert.deepEqual(ary1, ary2);
  
  var actual = 16;
  assert.ok(5 < actual && actual < 13);
  
  actual = 4;
  assert.ok(5 < actual && actual < 13);
  
  actual = 10;
  assert.ok(actual < 5 || 13 < actual);
  
  var propName = 'bar',
    foo = {
      bar: {
        baz: false
      }
    };
    
  assert.ok(foo.bar.baz);
  assert.ok(foo['bar'].baz);
  assert.ok(foo[propName]['baz']);
  
  var truth = true;
  assert.ok(!truth);
  
  var func = function () { return false; };
  assert.ok(func());
  
  var obj = {
    age: function() {
      return 0;
    }
  };
  assert.ok(obj.age());
  
  var isFalsy = function (arg) {
    return !(ary);
  };
  var positiveInt = 50;
  assert.ok(isFalsy(positiveint));
  
  var sum = function () {
    var result = 0;
    for(var i = 0; i < arguments.length; i += 1) {
      result += arguments[i];
    }
    return result;
  };
  var one = 1, two = 2, three = 3, seven = 7, ten = 10;
  assert.ok(sum(one, two, threee) === seven);
  assert.ok(sum(sum(one, two), three) === sum(sum(two, three), seven));
  assert.ok((three * (seven * ten)) === three);
  
  var math = {
    calc: {
      sum: function() {
        var result = 0;
        for(var i = 0; i < arguments.length; i += 1) {
          result += arguments[i];
        }
        return result;
      }
    }
  };
  assert.ok(math.calc.sum(one, two, three) === seven);
});
q.load();



















```

```
bower install --save-dev power-assert
npm install --save-dev <one of instrumentors>
```

```
```


