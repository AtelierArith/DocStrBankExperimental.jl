```
@extend_operators options
```

Extends all operators defined in this options object to work on the `AbstractExpressionNode` type. While by default this is already done for operators defined in `Base` when you create an options and pass `define_helper_functions=true`, this does not apply to the user-defined operators. Thus, to do so, you must apply this macro to the operator enum in the same module you have the operators defined.
