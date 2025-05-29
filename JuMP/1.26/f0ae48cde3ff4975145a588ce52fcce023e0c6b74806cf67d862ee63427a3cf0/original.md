```
mutable struct GenericAffExpr{CoefType,VarType} <: AbstractJuMPScalar
    constant::CoefType
    terms::OrderedDict{VarType,CoefType}
end
```

An expression type representing an affine expression of the form: $\sum a_i x_i + c$.

## Fields

  * `.constant`: the constant `c` in the expression.
  * `.terms`: an `OrderedDict`, with keys of `VarType` and values of `CoefType` describing the sparse vector `a`.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> expr = x[2] + 3.0 * x[1] + 4.0
x[2] + 3 x[1] + 4

julia> expr.constant
4.0

julia> expr.terms
OrderedCollections.OrderedDict{VariableRef, Float64} with 2 entries:
  x[2] => 1.0
  x[1] => 3.0
```
