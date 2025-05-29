Barber-Candès adjustment

# Examples

```jldoctest
julia> pvals = PValues([0.001, 0.01, 0.03, 0.5]);

julia> adjust(pvals, BarberCandes())
4-element Array{Float64,1}:
 0.3333333333333333
 0.3333333333333333
 0.3333333333333333
 1.0
```

# References

Barber, R.F., and Candès, E.J. (2015). Controlling the false discovery rate via knockoffs. Ann. Statist. 43, 2055–2085.

Arias-Castro, E., and Chen, S. (2017). Distribution-free multiple testing. Electron. J. Statist. 11, 1983–2001.
