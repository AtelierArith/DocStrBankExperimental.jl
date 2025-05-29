```
@call_rule NodeType(:edge, Constraint) (argument1 = value1, argument2 = value2, ..., [ meta = ..., addons = ... ])
```

The `@call_rule` macro helps to call the `rule` method with an easier syntax.  The structure of the macro is almost the same as in the `@rule` macro, but there is no `begin ... end` block, but instead each argument must have a specified value with the `=` operator.

The `@call_rule` accepts optional list of options before the functional form specification, for example:

```julia
@call_rule [ return_addons = true ] NodeType(:edge, Constraint) (argument1 = value1, argument2 = value2, ..., [ meta = ..., addons = ... ])
```

The list of available options is:

  * `return_addons` - forces the `@call_rule` to return the tuple of `(result, addons)`
  * `fallback` - specifies the fallback rule to use in case the rule is not defined for the given `NodeType` and specified arguments

See also: [`@rule`](@ref), [`rule`](@ref), [`@call_marginalrule`](@ref)
