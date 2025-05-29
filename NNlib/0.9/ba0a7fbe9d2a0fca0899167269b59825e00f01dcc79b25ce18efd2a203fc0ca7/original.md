```
∇upsample_bilinear(Δ::AbstractArray{T,4}; size::NTuple{2,Integer}, align_corners::Bool = true) where T
```

# Arguments

  * `Δ`: Incoming gradient array, backpropagated from downstream layers
  * `size`: Lateral (W,H) size of the image upsampled in the first place

# Outputs

  * `dx`: Downsampled version of `Δ`
