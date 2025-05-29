```
cut(x::AbstractArray, ngroups::Integer;
    labels::Union{AbstractVector{<:AbstractString},Function},
    allowempty::Bool=false)
```

Cut a numeric array into `ngroups` quantiles, determined using `quantile`.

If `x` contains `missing` values, they are automatically skipped when computing quantiles.

# Keyword arguments

  * `labels::Union{AbstractVector, Function}`: a vector of strings, characters or numbers giving the names to use for the intervals; or a function `f(from, to, i; leftclosed, rightclosed)` that generates the labels from the left and right interval boundaries and the group index. Defaults to `"Qi: [from, to)"` (or `"Qi: [from, to]"` for the rightmost interval).
  * `allowempty::Bool=false`: when `false`, an error is raised if some quantiles breakpoints are equal, generating empty intervals; when `true`, duplicate breaks are allowed and the intervals they generate are kept as unused levels (but duplicate labels are not allowed).
