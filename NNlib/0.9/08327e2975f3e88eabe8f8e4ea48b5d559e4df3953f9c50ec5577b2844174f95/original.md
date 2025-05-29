```
∇upsample_linear(Δ::AbstractArray{T,3}; size::Integer, align_corners::Bool = true) where T
```

# Arguments

  * `Δ`: Incoming gradient array, backpropagated from downstream layers
  * `size`: Size of the image upsampled in the first place

# Outputs

  * `dx`: Downsampled version of `Δ`
