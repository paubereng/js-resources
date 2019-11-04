# js-resources

### Easy way to convert string to number
```javascript
const string = '2';
const number = +string;

console.log(number)
// <- 2
```

### Double bang bang (double negation)
To ensure that everything that returns is a boolean value.
```javascript
const var_1 = null;
const var_2 = 0;
const var_3 = 1;
// Be careful with empty arrays and objects
const var_4 = {};
const var_5 = [];

console.log(!!var_1);
// <- false
console.log(!!var_2);
// <- false
console.log(!!var_3);
// <- true
console.log(!!var_4);
// <- true
console.log(!!var_5);
// <- true
```
### Remove duplicate values in array
Sets only allows unique values to be stored.
```javascript
const persons = ['Pau', 'Pau', 'Dani', 'Marc', 'Carlos'];
const newPersons = [...new Set(persons)];

console.log(newPersons);
// <- ['Pau','Dani','Marc','Carlos'];
```

### Rest operator
Get the object or array without some properties.
```javascript
const obj = {
  item1: 'item 1',
  item2: 'item 2',
  item3: 'item 3',
  item4: 'item 4',
};
const { item1, ...restItems } = obj;

console.log(restItems);
// <- {item2: 'item 2',item3: 'item 3',item4: 'item 4'}
```

### Deep destructuring
Get deepers properties inside an object.
```javascript
const obj = {
  item1: {
    subitem1: 'subitem 1',
  },
  item2: 'item 2',
  item3: 'item 3',
  item4: 'item 4',
};
const { item1: { subitem1 } } = obj;

console.log(subitem1);
// <- 'subitem 1'
```

### Object destructuring with arrays
```javascript
const persons = ['Pau', 'Dani', 'Marc', 'Carlos'];
const { 0: firstPerson, length, [length - 1]: lastPerson } = persons;

console.log(firstPerson);
// <- 'Pau'
console.log(length);
// <- 4
console.log(lastPerson);
// <- 'Carlos'
```

## Imutable
Primitive values (string or numbers) cannot be mutable by themselves. Objects and arrays are different, they are passed by reference.


### Wrong way (objects)
```javascript
const person = {
  name: 'Pau',
  age: 28,
};
const newPerson = person;
newPerson.age = 30;

console.log(person === newPerson);
// <- true
console.log(person);
// <- { name: 'Pau', age: 30 }
```

### Good way (objects)
Using spread operator or ```Object.assign```
```javascript
const person = {
  name: 'Pau',
  age: 28,
};
const newPerson = {
  ...person,
  age: 30,
}

console.log(person === newPerson);
// <- false
console.log(newPerson);
// <- { name: 'Pau', age: 30 }
console.log(person);
// <- { name: 'Pau', age: 28 }
```


### Wrong way (arrays)
```javascript
const persons = ['Pau', 'Dani'];
const newPersons = persons;
newPersons.push('David');

console.log(persons === newPersons);
// <- true
console.log(persons);
// <- ['Pau', 'Dani', 'David'];
```

### Good way (arrays)
Also you can use ```Filter``` and ```map```, without mutating state.
```javascript
const persons = ['Pau', 'Dani'];
const newPersons = [...persons, 'David']

console.log(persons === newPersons);
// <- false
console.log(persons);
// <- ['Pau', 'Dani'];
console.log(newPersons);
// <- ['Pau', 'Dani', 'David'];
```
