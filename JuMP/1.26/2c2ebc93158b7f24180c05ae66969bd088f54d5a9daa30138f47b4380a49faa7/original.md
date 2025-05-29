```
@constraint(model, expr, args...; kwargs...)
@constraint(model, [index_sets...], expr, args...; kwargs...)
@constraint(model, name, expr, args...; kwargs...)
@constraint(model, name[index_sets...], expr, args...; kwargs...)
```

Add a constraint described by the expression `expr`.

The `name` argument is optional. If index sets are passed, a container is built and the constraint may depend on the indices of the index sets.

The expression `expr` may be one of following forms:

  * `func in set`, constraining the function `func` to belong to the set `set`, which is either a [`MOI.AbstractSet`](@ref) or one of the JuMP shortcuts like [`SecondOrderCone`](@ref) or [`PSDCone`](@ref)
  * `a <op> b`, where `<op>` is one of `==`, `≥`, `>=`, `≤`, `<=`
  * `l <= f <= u` or `u >= f >= l`, constraining the expression `f` to lie between `l` and `u`
  * `f(x) ⟂ x`, which defines a complementarity constraint
  * `z --> {expr}`, which defines an indicator constraint that activates when `z` is `1`
  * `!z --> {expr}`, which defines an indicator constraint that activates when `z` is `0`
  * `z <--> {expr}`, which defines a reified constraint
  * `expr := rhs`, which defines a Boolean equality constraint

Broadcasted comparison operators like `.==` are also supported for the case when the left- and right-hand sides of the comparison operator are arrays.

JuMP extensions may additionally provide support for constraint expressions which are not listed here.

## Keyword arguments

  * `base_name`: sets the name prefix used to generate constraint names. It corresponds to the constraint name for scalar constraints, otherwise, the constraint names are set to `base_name[...]` for each index `...`.
  * `container = :Auto`: force the container type by passing `container = Array`,

`container = DenseAxisArray`, `container = SparseAxisArray`, or any another   container type which is supported by a JuMP extension.

  * `set_string_name::Bool = true`: control whether to set the [`MOI.ConstraintName`](@ref) attribute. Passing `set_string_name = false` can improve performance.

Other keyword arguments may be supported by JuMP extensions.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:3]);

julia> @variable(model, z, Bin);

julia> @constraint(model, x in SecondOrderCone())
[x[1], x[2], x[3]] ∈ MathOptInterface.SecondOrderCone(3)

julia> @constraint(model, [i in 1:3], x[i] == i)
3-element Vector{ConstraintRef{Model, MathOptInterface.ConstraintIndex{MathOptInterface.ScalarAffineFunction{Float64}, MathOptInterface.EqualTo{Float64}}, ScalarShape}}:
 x[1] = 1
 x[2] = 2
 x[3] = 3

julia> @constraint(model, x .== [1, 2, 3])
3-element Vector{ConstraintRef{Model, MathOptInterface.ConstraintIndex{MathOptInterface.ScalarAffineFunction{Float64}, MathOptInterface.EqualTo{Float64}}, ScalarShape}}:
 x[1] = 1
 x[2] = 2
 x[3] = 3

julia> @constraint(model, con_name, 1 <= x[1] + x[2] <= 3)
con_name : x[1] + x[2] ∈ [1, 3]

julia> @constraint(model, con_perp[i in 1:3], x[i] - 1 ⟂ x[i])
3-element Vector{ConstraintRef{Model, MathOptInterface.ConstraintIndex{MathOptInterface.VectorAffineFunction{Float64}, MathOptInterface.Complements}, VectorShape}}:
 con_perp[1] : [x[1] - 1, x[1]] ∈ MathOptInterface.Complements(2)
 con_perp[2] : [x[2] - 1, x[2]] ∈ MathOptInterface.Complements(2)
 con_perp[3] : [x[3] - 1, x[3]] ∈ MathOptInterface.Complements(2)

julia> @constraint(model, z --> {x[1] >= 0})
z --> {x[1] ≥ 0}

julia> @constraint(model, !z --> {2 * x[2] <= 3})
!z --> {2 x[2] ≤ 3}
```
