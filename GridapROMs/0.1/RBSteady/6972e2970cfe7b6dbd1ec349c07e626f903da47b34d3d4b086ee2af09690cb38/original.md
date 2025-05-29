```
contraction(Φₗₖ::AbstractArray{T,3},Aₖ::AbstractArray{T,3}) -> AbstractArray{T,4}
contraction(Φₗₖ::AbstractArray{T,3},Aₖ::AbstractArray{T,3},Φᵣₖ::AbstractArray{T,3}) -> AbstractArray{T,6}
```

Contraction of tensor train cores, as a result of a (Petrov-)Galerkin projection. The contraction of `Aₖ` by `Φₗₖ` is the left-contraction of a TT core `Aₖ` by a (left, test) TT core `Φₗₖ`, whereas the contraction of `Aₖ` by `Φᵣₖ` is the right-contraction of a TT core `Aₖ` by a (right, trial) TT core `Φᵣₖ`. The dimension of the output of a contraction involving `N` factors is: `3N - N = 2N`.
