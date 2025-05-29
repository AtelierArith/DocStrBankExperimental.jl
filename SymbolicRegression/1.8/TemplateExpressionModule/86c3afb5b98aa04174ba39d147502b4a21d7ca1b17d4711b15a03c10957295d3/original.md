```
TemplateStructure{K,E,NF} <: Function
```

A struct that defines a prescribed structure for a `TemplateExpression`, including functions that define the result in different contexts.

The `K` parameter is used to specify the symbols representing the inner expressions. If not declared using the constructor `TemplateStructure{K}(...)`, the keys of the `variable_constraints` `NamedTuple` will be used to infer this.

The `Kp` parameter is used to specify the symbols representing the parameters, if any.

# Fields

  * `combine`: Required function taking a `NamedTuple` of `ComposableExpression`s (sharing the keys `K`),   and then tuple representing the data of `ValidVector`s. For example,   `((; f, g), (x1, x2, x3)) -> f(x1, x2) + g(x3)` would be a valid `combine` function. You may also   re-use the callable expressions and use different inputs, such as   `((; f, g), (x1, x2)) -> f(x1 + g(x2)) - g(x1)` is another valid choice.
  * `num_features`: Optional `NamedTuple` of function keys => integers representing the number of   features used by each expression. If not provided, it will be inferred using the `combine`   function. For example, if `f` takes two arguments, and `g` takes one, then   `num_features = (; f=2, g=1)`.
  * `num_parameters`: Optional `NamedTuple` of parameter keys => integers representing the number of   parameters required for each parameter vector.
