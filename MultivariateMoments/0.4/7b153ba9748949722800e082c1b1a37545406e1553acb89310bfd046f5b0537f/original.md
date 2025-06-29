```
struct MacaulayNullspace{T,MT<:AbstractMatrix{T},BT}
    matrix::MT
    basis::BT
    accuracy::T
end
```

This matrix with rows indexed by `basis` can either be interpreted as the right null space of a Macaulay matrix with columns indexed by `basis` (resp. or the image space of a moment matrix with rows and columns indexed by `basis`). The value of `matrix[i, j]` should be interpreted as the value of the `i`th element of `basis` for the `j`th generator of the null space (resp. image) space.
