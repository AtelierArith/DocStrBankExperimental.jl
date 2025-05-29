```
BracketAlgebraElem{T<:Union{RingElem,Number}} <: AbstractBracketAlgebraElem{T}
```

Element type for [`BracketAlgebra`](@ref) with coefficients of type `T`.

# Fields

  * `parent::BracketAlgebra{T}`: parent object of the bracket algebra element.
  * `polynomial::MPolyRingElem{T}`: polynomial in `parent.R` that represents the element.
