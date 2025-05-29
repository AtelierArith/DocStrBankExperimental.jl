```
@explicit_intercepts(f::Symbol, type_tuple::Expr, is_node::Expr[, kwargs::Expr])
@explicit_intercepts(f::Symbol, type_tuple::Expr)
```

Create a collection of methods which intecept the function calls to `f` in which at least one argument is a `Node`. Types of arguments are specified by the type tuple expression in `type_tuple`. If there are arguments which are not differentiable, they can be specified by providing a boolean vector `is_node` which indicates those arguments that are differentiable with `true` values and those which are not as `false`. Keyword arguments to add to the function signature can be specified in `kwargs`, which must be a `NamedTuple`.
