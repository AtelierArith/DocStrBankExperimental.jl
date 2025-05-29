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
