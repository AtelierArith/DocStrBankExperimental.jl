```
∇upsample_trilinear(Δ::AbstractArray{T,5}; size::NTuple{3,Integer}, align_corners::Bool = true) where T
```

# Arguments

  * `Δ`: Incoming gradient array, backpropagated from downstream layers
  * `size`: Lateral size & depth (W,H,D) of the image upsampled in the first place

# Outputs

  * `dx`: Downsampled version of `Δ`
