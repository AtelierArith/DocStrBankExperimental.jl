```
unwrapresult(think::Think)
```

Unwrap the retrieved result of a `think` object.

This function extracts the result of a `Think` object from its `Some` container. If the `Think` object has not been reified (i.e., `reify!` has not been called) or is still running, it throws an error.
