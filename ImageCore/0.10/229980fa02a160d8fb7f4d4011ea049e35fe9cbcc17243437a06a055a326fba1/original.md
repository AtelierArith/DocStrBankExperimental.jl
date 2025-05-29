```
takemap(f, A) -> fnew
takemap(f, T, A) -> fnew
```

Given a value-mapping function `f` and an array `A`, return a "concrete" mapping function `fnew`. When applied to elements of `A`, `fnew` should return valid values for storage or display, for example in the range from 0 to 1 (for grayscale) or valid colorants. `fnew` may be adapted to the actual values present in `A`, and may not produce valid values for any inputs not in `A`.

Optionally one can specify the output type `T` that `fnew` should produce.

# Example:

```julia
julia> A = [0, 1, 1000];

julia> f = takemap(scaleminmax, A)
(::#7) (generic function with 1 method)

julia> f.(A)
3-element Array{Float64,1}:
 0.0
 0.001
 1.0
```
