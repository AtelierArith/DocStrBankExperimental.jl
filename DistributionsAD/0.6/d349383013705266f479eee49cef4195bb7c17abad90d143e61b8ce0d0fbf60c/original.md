```
filldist(d::Distribution, ns...)
```

Create a product distribution from a single distribution and a list of dimension sizes. If `size(d)` is `(d1, d2, ...)` and `ns` is `(n1, n2, ...)`, then the resulting distribution will have size `(d1, d2, ..., n1, n2, ...)`.

The default behaviour is to use [`Distributions.product_distribution`](https://juliastats.org/Distributions.jl/stable/multivariate/#Distributions.product_distribution), with `FillArrays.Fill` supplied as the array argument. However, this behaviour is specialised in some instances, such as the one shown below.

When sampling from the resulting distribution, the output will be an array where each element is sampled from the original distribution `d`.

# Examples

```jldoctest; setup=:(using Distributions, Random)
julia> d = filldist(Normal(0, 1), 4, 5);

julia> size(d)
(4, 5)

julia> rand(d) isa Matrix{Float64}
true
```
