```
ForceIntensity(
    ::Type{T},
    ndofn,
    computeforce!::F,
) where {T<:Number, F<:Function}
```

Construct force intensity when the function to compute the intensity vector is given.

# Arguments

  * `T` = the type of the elements of the force vector, typically floating-point or complex floating-point numbers,
  * `ndofn` = number of elements of the force vector (the length of the force vector),
  * `computeforce!` = callback function. The function `computeforce!` needs to have a signature of   `function computeforce!(forceout::Vector{CT}, XYZ::Matrix{T},       tangents::Matrix{T}, feid::IT) ) where {CT, T<:Number, IT<:Integer}       # Calculate the force  and copy it into the buffer forceout....       return forceout   end`   and it needs to fill in the buffer `forceout` with the current force at the   location `XYZ`, using, if appropriate, the information supplied in the Jacobian   matrix `tangents`, and the identifier of the finite element, `feid`.
