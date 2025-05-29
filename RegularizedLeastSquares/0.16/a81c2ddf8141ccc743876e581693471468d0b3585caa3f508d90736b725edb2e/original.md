```
TransformedRegularization(reg, trafo)
```

Nested regularization term that applies `prox!` or `norm` on `z = trafo * x` and returns (inplace) `x = adjoint(trafo) * z`.

# Example

```julia
julia> core = L1Regularization(0.8)
L1Regularization{Float64}(0.8)

julia> wop = WaveletOp(Float32, shape = (32,32));

julia> reg = TransformedRegularization(core, wop);

julia> prox!(reg, randn(32*32)); # Apply soft-thresholding in Wavelet domain
```
