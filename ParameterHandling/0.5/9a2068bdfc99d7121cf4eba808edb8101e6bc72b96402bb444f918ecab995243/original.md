```
deferred(f, args...)
```

The `value` of a `deferred` is `f(value(args)...)`. This makes it possible to make the value of the `args` e.g. `AbstractParameter`s and, therefore, enforce constraints on them even if `f` knows nothing about `AbstractParameters`.

It can be helpful to use `deferred` recursively when constructing complicated objects.
