```
SurfaceNormal(ndimensions, z::T, computenormal!::F) where {T<:Number, F<:Function}
```

Construct surface normal evaluator when the function to compute the normal vector is given.

# Arguments

  * `T` = the type of the elements of the normal vector,
  * `ndofn` = number of components of the normal vector,
  * `computenormal!` = callback function. The function `computenormal!` needs to have a signature of

    `function computenormal!(normalout::Vector{CT}, XYZ::AbstractVecOrMat{<:Real},       tangents::AbstractMatrix{<:Real}, feid::IT, qpid::IT) where {CT, IT}       # Calculate the normal  and copy it into the buffer....       return normalout   end`

    and it needs to  fill in the buffer `normalout` with the current normal at   the location `XYZ`, using, if appropriate, the information supplied in the   Jacobian matrix `tangents`, the identifier of the finite element, `feid`,   and the quadrature point id, `qpid`. Refer to [`DataCache`](@ref).
