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
