```
SurfaceNormal{F<:Function}
```

Exterior surface normal type.

The normal vector is assumed to be normalized to unit length.

Signature of the function to compute the value of the unit normal at any given point `XYZ`, using the columns of the Jacobian matrix of the element, `tangents`,  the finite element label, `feid`, and the identifier of the quadrature point, `qpid`:

```
function computenormal!(normalout::Vector{CT}, XYZ::AbstractVecOrMat{<:Real},
    tangents::AbstractMatrix{<:Real}, feid::IT, qpid::IT) where {CT, IT}
    # Calculate the normal  and copy it into the buffer....
    return normalout
end
```

The buffer `normalout` needs to be filled with the value  of the normal vector.

Refer to [`DataCache`](@ref) for details on the caching.
