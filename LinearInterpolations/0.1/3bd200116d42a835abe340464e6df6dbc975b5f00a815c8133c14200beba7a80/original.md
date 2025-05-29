```
itp = Interpolate(axes, values; combine = LinearInterpolations.combine, extrapolate = :error)
```

Create an `Interpolate` from the given arguments. The interpolate `itp` can be evaluated on points. E.g. `itp([1,2])`.

# Arguments

  * axes: The coordinates of the grid points.
  * values: An AbstractArray which whose size is consistent with the length each axis.
  * extrapolate: How the interpolate behaves on points outside the grid limits. Possible values are:

      * [`Replicate`](@ref), `:replicate`
      * [`Reflect`](@ref), `:reflect`
      * [`Error`](@ref), `:error`
      * [`Fuzzy`](@ref), `:fuzzy`
      * [`WithPoint`](@ref)
      * [`Constant`](@ref)
  * combine: A custom function that combines weights and values into the final result.

See [`LinearInterpolations.combine`](@ref)
