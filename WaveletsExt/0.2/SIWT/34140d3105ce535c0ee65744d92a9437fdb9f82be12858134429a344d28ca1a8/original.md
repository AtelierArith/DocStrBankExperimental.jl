```
ShiftInvariantWaveletTransformNode{N, T₁<:Integer, T₂<:AbstractFloat}
```

Data structure to hold the index, coefficients, and cost value of an SIWT node.

# Parameters

  * `Depth::T₁`: The depth of current node. Root node has depth 0.
  * `IndexAtDepth::T₁`: The node index at current depth. Index starts from 0 at each depth.
  * `TransformShift::T₁`: The type of shift operated on the parent node before computing the transform. Accepted type of shift values are:

      * `0`: Coefficients of parent node are not shifted prior to transform.
      * `1`: For both 1D and 2D signals, coefficients of parent node are circularly shifted to  the left by 1 index.
      * `2`: For 2D signals, coefficients of parent node are circularly shifted from bottom to top by 1 index. Not available for 1D signals.
      * `3`: For 2D signals, coefficients of parent node are circularly shifted from bottom to top and right to left by 1 index each. Not available for 1D signals.
  * `Cost::T₂`: The [`ShannonEntropyCost`](@ref) of current node.
  * `Value::Array{T₂,N}`: Coefficients of current node.

**See also:** [`ShiftInvariantWaveletTransformObject`](@ref)
