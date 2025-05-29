```
@disjunction(model, expr, kw_args...)
```

Add a disjunction described by the expression `expr`,  which must be a `Vector` of `LogicalVariableRef`s.

```
@disjunction(model, ref[i=..., j=..., ...], expr, kw_args...)
```

Add a group of disjunction described by the expression `expr` parameterized by `i`, `j`, ..., which must be a `Vector` of `LogicalVariableRef`s. 

In both of the above calls, a [`Disjunct`](@ref) tag can be added to create  nested disjunctions.

The recognized keyword arguments in `kw_args` are the following:

  * `base_name`: Sets the name prefix used to generate constraint names.    It corresponds to the constraint name for scalar constraints, otherwise,    the constraint names are set to `base_name[...]` for each index `...`        of the axes `axes`.
  * `container`: Specify the container type.
  * `exactly1`: Specify a `Bool` whether a constraint should be added to   only allow selecting one disjunct in the disjunction.

To create disjunctions without macros, see [`disjunction`](@ref).
