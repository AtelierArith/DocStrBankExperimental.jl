```
∇upsample_nearest(Δ::AbstractArray{T,3}, scales::NTuple{S, <:Integer}) where T
```

# Arguments

  * `Δ`: Incoming gradient array, backpropagated from downstream layers
  * `scales`: scales by which the image was upsampled in the first place

# Outputs

  * `dx`: Downsampled version of `Δ`
