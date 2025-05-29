```
adjust_histogram([T::Type,] img, f::AbstractHistogramAdjustmentAlgorithm, args...; kwargs...)
```

Adjust histogram of `img` using algorithm `f`.

# Output

The return image `img_adjusted` is an `Array{T}`.

If `T` is not specified, then it's inferred.

# Examples

Just simply pass the input image and algorithm to `adjust_histogram`

```julia
img_adjusted = adjust_histogram(img, f)
```

This reads as "`adjust_histogram` of image `img` using algorithm `f`".

You can also explicitly specify the return type:

```julia
img_adjusted_float32 = adjust_histogram(Gray{Float32}, img, f)
```

See also [`adjust_histogram!`](@ref) for in-place histogram adjustment.
