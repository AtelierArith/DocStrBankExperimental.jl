```
ShiftInvariantWaveletTransformNode(data, depth, indexAtDepth, transformShift)
```

Outer constructor of SIWT node.

# Arguments

  * `data::Array{T} where T<:AbstractFloat`: Array of coefficients.
  * `depth::S where S<:Integer`: Depth of current node.
  * `indexAtDepth::S where S<:Integer`: Node index at current depth.
  * `transformShift::S where S<:Integer`: The type of shift operated on the parent node before computing the transform.
  * `nrm::T where T<:AbstractFloat`: (Default: `norm(data)`) Norm of the signal.
