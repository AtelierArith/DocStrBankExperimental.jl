```
@union_intercepts f type_tuple invoke_type_tuple [kwargs]
```

Interception strategy based on adding a method to `f` which accepts the union of each of the types specified by `type_tuple`. If none of the arguments are `Node`s then the method of `f` specified by `invoke_type_tuple` is invoked. If applicable, keyword arguments should be provided as a `NamedTuple` and be added to the generated function's signature.
