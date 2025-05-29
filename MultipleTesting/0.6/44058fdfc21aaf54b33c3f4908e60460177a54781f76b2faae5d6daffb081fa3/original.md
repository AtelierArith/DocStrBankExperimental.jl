Stouffer's p-value combination

# Examples

```jldoctest
julia> pvals = PValues([0.01, 0.02, 0.3, 0.5]);

julia> combine(pvals, Stouffer())
0.00709832618126593

julia> weights = [1.0, 2.0, 0.4, 1.5];

julia> combine(pvals, weights, Stouffer())
0.007331653763696742
```

# References

Stouffer, S.A. (1949). The American soldier. Vol. 1: Adjustment during army life (Princeton University Press).

Liptak, T. (1958). On the combination of independent tests. Magyar Tud Akad Mat Kutato Int Kozl 3, 171–197.
