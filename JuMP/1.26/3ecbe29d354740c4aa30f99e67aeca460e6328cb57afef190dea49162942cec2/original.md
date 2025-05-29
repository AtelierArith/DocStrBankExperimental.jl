```
UnorderedPair(a::T, b::T)
```

A wrapper type used by [`GenericQuadExpr`](@ref) with fields `.a` and `.b`.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> expr = 2.0 * x[1] * x[2]
2 x[1]*x[2]

julia> expr.terms
OrderedCollections.OrderedDict{UnorderedPair{VariableRef}, Float64} with 1 entry:
  UnorderedPair{VariableRef}(x[1], x[2]) => 2.0
```
