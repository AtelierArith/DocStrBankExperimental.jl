```
ArrayAxes{N}
```

is the canonical type of array axes as returned by the base method `axes(A::AbstractArray)`. It is an `N`-tuple of [`ArrayAxis`](@ref) instances. Method [`as_array_axes`](@ref) may be called to convert arguments to array axes.

See also [`ArrayShape`](@ref), `Dims`.
