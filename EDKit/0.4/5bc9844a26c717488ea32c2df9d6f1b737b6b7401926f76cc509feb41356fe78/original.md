```
index(dgt::AbstractVector{T}; base::Integer=2, dtype::DataType=T) where T <: Integer
```

Convert a digits to the integer index using the relation: 

```
number = ∑ᵢ bits[i] * base^(L-i) + 1
```

The summaton is evaluate using the efficieint polynomial evaluation method.

## Inputs:

  * `dgt`  : Digits.
  * `base` : Base.
