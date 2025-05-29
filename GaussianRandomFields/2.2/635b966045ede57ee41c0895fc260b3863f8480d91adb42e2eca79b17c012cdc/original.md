```
randdim(grf)
```

Returns the number of random numbers used to sample from the Gaussian random field `grf`.

# Examples

```jldoctest
julia> cov = CovarianceFunction(2, Whittle(.1))
2d Whittle covariance function (λ=0.1, σ=1.0, p=2.0)

julia> pts = pts = range(0, stop=1, length=51)
0.0:0.02:1.0

julia> grf = GaussianRandomField(cov, KarhunenLoeve(200), pts, pts)
Gaussian random field with 2d Whittle covariance function (λ=0.1, σ=1.0, p=2.0) on a 51×51 structured grid, using a KL expansion with 200 terms

julia> randdim(grf)
200

```
