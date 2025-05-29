```
  lcc(haystack,needle)
```

Calculate the local (Pearson) correlation coefficients between a `needle` and a sliding window within `haystack`, directly.

# Example

Suppose you have a `haystack`, a tensor of reals and a `needle`, a smaller tensor of the same dimensionality that you are are trying to locate in the `haystack`. Note that the `needle` might be scaled and translated.

The position of the maximum LCC is the best match between the `needle` and a sliding window of `haystack`

```jldoctest
julia> using FastLocalCorrelationCoefficients

julia> haystack = rand(2^10,2^10);

julia> needle = rand(1) .* haystack[42:47, 45:50] .+ rand(1);

julia> c = lcc(haystack,needle);

julia> best_correlated(c)
CartesianIndex(42, 45)
```
