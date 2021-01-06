---
title: "To-do list Web App"
date: 2021-01-05T23:27:23-06:00
draft: false
---

I made a todo list web app to refesh my knowledge of react.js and django.

Stack:

- React.js
- Django
- Django REST framework

### [Demo](https://www.youtube.com/watch?v=Kj2Iw1EYI7Q)

[![Watch the video](https://j.gifs.com/E8zDl0.gif)](https://www.youtube.com/watch?v=Kj2Iw1EYI7Q)

[check on github](https://github.com/xiaotonghe/Todo-app)

### What I learned from the project:

Here are some important notes of React.js:

1. Two different ways to create React component:

- Stateless functional component;
- Class component.

2. props V.S. state

- props receives input from react component and it's not allowed to change them;
- state is data that changes over time and only class component has state.

3. "this" keyword

- example 1:

"this" refers to the Component/Class (Test) itself, the concept is similar to the "self" concept from an object of Python.

```
class Test extends Component {
  constructor() {
    super();
    this.name = 'Xiaotong';
  }
  componentDidMount() {
    console.log(this.name);
  }
  render() {
    return null;
  }
}
```

- example 2:

"this" refers to how a function is being called. `clickFunction` is a a callback function to a click handler and the event handler is actully called by window. So `bind` method is used to bind the function to Component/Class App. If you get rid of `this` here, you'll get an error: `'clickFunction' is not defined`.

```
import React, { Component } from 'react';
class App extends Component {
  constructor(props) {
    super(props);
    this.clickFunction = this.clickFunction.bind(this);
  }
  clickFunction() {
    console.log(this.props.value);
  }
  render() {
    return(
      <div onClick={this.clickFunction}>Click Me!</div>
    );
  }
}
```

You can also write `clickFuction` as an arrow function:

```
import React, { Component } from 'react';
class App extends Component {
  clickFunction = () => {
    console.log(this.props.value);
  }
  render() {
    return(
      <div onClick={this.clickFunction}>Click Me!</div>
    );
  }
}
```

Since `clickFunction` is now an arrow function, it'll automatically bind the value of this to its current scope, and you don't have to worry about it changing depending on who's calling that function.
