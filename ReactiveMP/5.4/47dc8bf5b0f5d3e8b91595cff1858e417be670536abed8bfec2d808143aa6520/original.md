```
constrain_form(wrapped::WrappedFormConstraint, something)
```

This function unwraps the `wrapped` object and calls `constrain_form` function with the provided context. If the context is not provided, simply calls `constrain_form` with the wrapped constraint. Otherwise passes the context to the `constrain_form` function as the second argument.
