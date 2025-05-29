```
get_wigner_array(w::AbstractWigner{T}) where {T}
```

Utility function for getting an OffsetArray with indices from jₘᵢₙ to jₘₐₓ.

# Arguments

  * `w::AbstractWigner{T}`: contains the quantum numbers and dispatches on the kind of symbol

# Returns

  * `OffsetArray{T}`: an array for wigner symbols
