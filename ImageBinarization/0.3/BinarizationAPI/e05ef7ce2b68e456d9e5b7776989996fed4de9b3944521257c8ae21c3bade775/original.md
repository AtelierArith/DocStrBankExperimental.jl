```
binarize!([out,] img, f::AbstractImageBinarizationAlgorithm, args...; kwargs...)
```

Binarize `img` using algorithm `f`.

# Output

If `out` is specified, it will be changed in place. Otherwise `img` will be changed in place.

# Examples

Just simply pass an algorithm to `binarize!`:

```julia
img₀₁ = similar(img)
binarize!(img₀₁, img, f)
```

For cases you just want to change `img` in place, you don't necessarily need to manually allocate `img₀₁`; just use the convenient method:

```julia
binarize!(img, f)
```

See also: [`binarize`](@ref)
