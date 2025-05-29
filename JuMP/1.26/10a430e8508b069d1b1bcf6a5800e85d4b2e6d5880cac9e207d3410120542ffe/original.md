```
mutable struct GenericQuadExpr{CoefType,VarType} <: AbstractJuMPScalar
    aff::GenericAffExpr{CoefType,VarType}
    terms::OrderedDict{UnorderedPair{VarType}, CoefType}
end
```

An expression type representing an quadratic expression of the form: $\sum q_{i,j} x_i x_j + \sum a_i x_i + c$.

## Fields

  * `.aff`: an [`GenericAffExpr`](@ref) representing the affine portion of the expression.
  * `.terms`: an `OrderedDict`, with keys of `UnorderedPair{VarType}` and values of `CoefType`, describing the sparse list of terms `q`.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> expr = 2.0 * x[1]^2 + x[1] * x[2] + 3.0 * x[1] + 4.0
2 x[1]² + x[1]*x[2] + 3 x[1] + 4

julia> expr.aff
3 x[1] + 4

julia> expr.terms
OrderedCollections.OrderedDict{UnorderedPair{VariableRef}, Float64} with 2 entries:
  UnorderedPair{VariableRef}(x[1], x[1]) => 2.0
  UnorderedPair{VariableRef}(x[1], x[2]) => 1.0
```
