```
decompress(epca::EPCA, A::AbstractMatrix{T}) where T <: Real
```

Decompress the compressed matrix `A` with the EPCA model.

# Arguments

  * `epca::EPCA`: The fitted EPCA model.[^1] `fit!` should be called before `compress`.
  * `A::AbstractMatrix{T}`: (`n`, `outdim`) - A compressed data matrix.

# Returns

  * `X̂::AbstractMatrix{T}`: (`n`, `indim`) - The reconstructed data matrix approximated using EPCA model parameters.

# Usage

```julia
Y_reconstructed = decompress(epca, Y)
```
