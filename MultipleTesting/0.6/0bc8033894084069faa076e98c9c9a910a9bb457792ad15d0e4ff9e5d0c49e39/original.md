Fisher's p-value combination

# Examples

```jldoctest
julia> pvals = PValues([0.01, 0.02, 0.3, 0.5]);

julia> combine(pvals, Fisher())
0.007616871850449092
```

# References

Fisher, R.A. (1925). Statistical methods for research workers (Genesis Publishing Pvt Ltd).
