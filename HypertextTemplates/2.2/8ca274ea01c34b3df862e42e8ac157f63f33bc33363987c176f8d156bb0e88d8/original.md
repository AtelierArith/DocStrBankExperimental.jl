```
@deftag macro name end
@deftag name
```

Create a macro version of the given element or component called `name`. This is a shorthand way to call the `@<` macro with the given `name` while still correctly passing the source information through to the renderer. The `macro` variant allows the LSP to correctly infer the location of the definition whereas the plain symbol variant does not.
