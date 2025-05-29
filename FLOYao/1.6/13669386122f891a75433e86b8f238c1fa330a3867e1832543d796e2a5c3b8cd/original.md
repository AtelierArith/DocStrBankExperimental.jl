```
MajoranaReg{T} <: AbstractRegister{2}
MajoranaReg(state::AbstractMatrix{T<:Real})
```

A register holding the "state" of a Majorana operators when propagating through a FLO circuit as a `2n×2n` matrix.

# Warning

The `MajoranaReg` constructor will not initialize the `state` matrix. It is  recommended to use `FLOYao.zero_state` or `FLOYao.product_state` to produce your initial state.
