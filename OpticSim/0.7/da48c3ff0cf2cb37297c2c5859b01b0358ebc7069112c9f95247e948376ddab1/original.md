```
HierarchicalImage{T<:Number} <: AbstractArray{T,2}
```

Image type which dynamically allocated memory for pixels when their value is set, the value of unset pixels is assumed to be zero.

This is used for the detector image of [`AbstractOpticalSystem`](@ref)s which can typically be very high resolution, but often have a large proportion of the image blank.
