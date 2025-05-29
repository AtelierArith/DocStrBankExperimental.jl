```
@call_marginalrule NodeType(:edge) (argument1 = value1, argument2 = value2, ..., [ meta = ... ])
```

The `@call_marginalrule` macro helps to call the `marginalrule` method with an easier syntax.  The structure of the macro is almost the same as in the `@marginalrule` macro, but there is no `begin ... end` block,  but instead each argument must have a specified value with the `=` operator.

See also: [`@marginalrule`](@ref), [`marginalrule`](@ref), [`@call_rule`](@ref)
