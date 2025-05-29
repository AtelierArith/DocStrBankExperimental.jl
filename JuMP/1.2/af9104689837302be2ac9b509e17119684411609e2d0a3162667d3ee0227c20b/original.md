```
@constraint(m::Model, expr, kw_args...)
```

Add a constraint described by the expression `expr`.

```
@constraint(m::Model, ref[i=..., j=..., ...], expr, kw_args...)
```

Add a group of constraints described by the expression `expr` parametrized by `i`, `j`, ...

The expression `expr` can either be

  * of the form `func in set` constraining the function `func` to belong to the set `set` which is either a [`MOI.AbstractSet`](https://jump.dev/MathOptInterface.jl/v0.6.2/apireference.html#Sets-1) or one of the JuMP shortcuts [`SecondOrderCone`](@ref), [`RotatedSecondOrderCone`](@ref) and [`PSDCone`](@ref), e.g. `@constraint(model, [1, x-1, y-2] in SecondOrderCone())` constrains the norm of `[x-1, y-2]` be less than 1;
  * of the form `a sign b`, where `sign` is one of `==`, `≥`, `>=`, `≤` and `<=` building the single constraint enforcing the comparison to hold for the expression `a` and `b`, e.g. `@constraint(m, x^2 + y^2 == 1)` constrains `x` and `y` to lie on the unit circle;
  * of the form `a ≤ b ≤ c` or `a ≥ b ≥ c` (where `≤` and `<=` (resp. `≥` and `>=`) can be used interchangeably) constraining the paired the expression `b` to lie between `a` and `c`;
  * of the forms `@constraint(m, a .sign b)` or `@constraint(m, a .sign b .sign c)` which broadcast the constraint creation to each element of the vectors.

The recognized keyword arguments in `kw_args` are the following:

  * `base_name`: Sets the name prefix used to generate constraint names. It corresponds to the constraint name for scalar constraints, otherwise, the constraint names are set to `base_name[...]` for each index `...` of the axes `axes`.
  * `container`: Specify the container type.
  * `set_string_name::Bool = true`: control whether to set the [`MOI.ConstraintName`](@ref) attribute. Passing `set_string_name = false` can improve performance.

## Note for extending the constraint macro

Each constraint will be created using `add_constraint(m, build_constraint(_error, func, set))` where

  * `_error` is an error function showing the constraint call in addition to the error message given as argument,
  * `func` is the expression that is constrained
  * and `set` is the set in which it is constrained to belong.

For `expr` of the first type (i.e. `@constraint(m, func in set)`), `func` and `set` are passed unchanged to `build_constraint` but for the other types, they are determined from the expressions and signs. For instance, `@constraint(m, x^2 + y^2 == 1)` is transformed into `add_constraint(m, build_constraint(_error, x^2 + y^2, MOI.EqualTo(1.0)))`.

To extend JuMP to accept new constraints of this form, it is necessary to add the corresponding methods to `build_constraint`. Note that this will likely mean that either `func` or `set` will be some custom type, rather than e.g. a `Symbol`, since we will likely want to dispatch on the type of the function or set appearing in the constraint.

For extensions that need to create constraints with more information than just `func` and `set`, an additional positional argument can be specified to `@constraint` that will then be passed on `build_constraint`. Hence, we can enable this syntax by defining extensions of `build_constraint(_error, func, set, my_arg; kw_args...)`. This produces the user syntax: `@constraint(model, ref[...], expr, my_arg, kw_args...)`.
