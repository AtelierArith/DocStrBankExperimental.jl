```
decode_hilbert_zero!(ha::HilbertAlgorithm{T}}, X::Vector{A}, h::T)
```

Given a Hilbert index, `h`, computes an n-dimensional coordinate `X`. The type of the Hilbert index is large enought to contain the bits of all dimensions of the axis vector, `X`.
