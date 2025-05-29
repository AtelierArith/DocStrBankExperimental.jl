```
@expression(model::GenericModel, expression)
@expression(model::GenericModel, [index_sets...], expression)
@expression(model::GenericModel, name, expression)
@expression(model::GenericModel, name[index_sets...], expression)
```

Efficiently builds and returns an expression.

The `name` argument is optional. If index sets are passed, a container is built and the expression may depend on the indices of the index sets.

## Keyword arguments

  * `container = :Auto`: force the container type by passing `container = Array`, `container = DenseAxisArray`, `container = SparseAxisArray`, or any another container type which is supported by a JuMP extension.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:5]);

julia> @expression(model, shared, sum(i * x[i] for i in 1:5))
x[1] + 2 x[2] + 3 x[3] + 4 x[4] + 5 x[5]

julia> shared
x[1] + 2 x[2] + 3 x[3] + 4 x[4] + 5 x[5]
```

In the same way as [`@variable`](@ref), the second argument may define index sets, and those indices can be used in the construction of the expressions:

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:3]);

julia> @expression(model, expr[i = 1:3], i * sum(x[j] for j in 1:3))
3-element Vector{AffExpr}:
 x[1] + x[2] + x[3]
 2 x[1] + 2 x[2] + 2 x[3]
 3 x[1] + 3 x[2] + 3 x[3]
```

Anonymous syntax is also supported:

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:3]);

julia> expr = @expression(model, [i in 1:3], i * sum(x[j] for j in 1:3))
3-element Vector{AffExpr}:
 x[1] + x[2] + x[3]
 2 x[1] + 2 x[2] + 2 x[3]
 3 x[1] + 3 x[2] + 3 x[3]
```
