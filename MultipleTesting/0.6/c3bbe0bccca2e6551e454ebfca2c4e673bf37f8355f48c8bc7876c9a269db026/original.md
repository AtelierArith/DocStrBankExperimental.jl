Šidák adjustment

# Examples

```jldoctest
julia> pvals = PValues([0.001, 0.01, 0.03, 0.5]);

julia> adjust(pvals, Sidak())
4-element Array{Float64,1}:
 0.003994003998999962
 0.039403990000000055
 0.11470719000000007
 0.9375

julia> adjust(pvals, 6, Sidak())
4-element Array{Float64,1}:
 0.0059850199850060015
 0.058519850599
 0.1670279950710002
 0.984375
```

# References

Šidák, Z. (1967). Rectangular Confidence Regions for the Means of Multivariate Normal Distributions. Journal of the American Statistical Association 62, 626–633.
