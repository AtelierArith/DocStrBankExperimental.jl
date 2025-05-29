```
adjust_histogram!([out,] img, f::AbstractHistogramAdjustmentAlgorithm, args...; kwargs...)
```

Adjust histogram of `img` using algorithm `f`.

# Output

If `out` is specified, it will be changed in place. Otherwise `img` will be changed in place.

# Examples

Just simply pass an algorithm to `adjust_histogram!`:

```julia
img_adjusted = similar(img)
adjust_histogram!(img_adjusted, img, f)
```

For cases you just want to change `img` in place, you don't necessarily need to manually allocate `img_adjusted`; just use the convenient method:

```julia
adjust_histogram!(img, f)
```

See also: [`adjust_histogram`](@ref)
