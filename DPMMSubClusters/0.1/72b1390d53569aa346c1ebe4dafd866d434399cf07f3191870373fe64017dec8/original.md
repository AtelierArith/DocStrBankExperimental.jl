```
generate_gaussian_data(N::Int64, D::Int64, K::Int64,MixtureVar::Number)
```

Generate `N` observations, generated from `K` `D` dimensions Gaussians, with the Gaussian means sampled from a `Normal` distribution with mean `0` and `MixtureVar` variance.

Returns `(Samples, Labels, Clusters_means, Clusters_cov)`

# Example

```julia
julia> x,y,clusters = generate_gaussian_data(10000,2,6,100.0)
[3644, 2880, 119, 154, 33, 3170]
...
```
