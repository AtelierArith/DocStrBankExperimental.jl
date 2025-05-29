```
@cacheable timeout function_definition::ReturnType
```

For a function definition (`function_definition`, either short-form or full), create an `ExpiringCaches.Cache` and store results for `timeout` (hashed by the exact input arguments obviously).

Note that the function definition *MUST* include the `ReturnType` declartion as this is used as the value (`V`) type in the `Cache`.
