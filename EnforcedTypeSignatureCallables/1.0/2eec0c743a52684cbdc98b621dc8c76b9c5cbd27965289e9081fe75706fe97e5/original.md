```
TypedCallable
```

A simple callable type wrapping another callable.

There are three type parameters: the first type parameter represents the allowed types of the positional arguments. The second type parameter is the allowed return type of the callable. The third type parameter is the type of the wrapped callable.

The first type parameter, representing the allowed positional argument types, always subtypes `Tuple`. For example, to allow either a single `Int` argument or two `Bool` arguments, choose `Union{Tuple{Int},Tuple{Bool,Bool}}` as the first type parameter.

To disable argument type checking, just choose `Tuple` as the first parameter.

To disable return type checking, just choose `Any`, as the second parameter.
