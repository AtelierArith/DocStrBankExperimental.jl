```
@render [destination] dom
```

Renders the `dom` tree to the `destination` object. When no `destination` is provided then the `dom` is rendered directly to `String` and returned as the value of the expression.

This is only needed for rendering the root of the DOM tree, not for the output of each individual component that is defined.
