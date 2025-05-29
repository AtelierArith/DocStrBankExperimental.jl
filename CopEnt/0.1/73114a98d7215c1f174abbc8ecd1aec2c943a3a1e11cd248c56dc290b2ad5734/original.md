```julia
copula_entropy(x; kwargs...)

```

Estimate the copula entropy by

1. Compute the emperical copula (see also [`empirical_copula`](@ref));
2. Estimate the entropy using the Kraskov method (see [`entropy_knn`](@ref) for keyword parameters) [1].

The returned copula entropy is the negative mutual information [2].

# References

1. Alexander Kraskov, Harald Stögbauer and Peter Grassberger. "Estimating mutual information." Physical review, 2004.
2. Jian Ma and Zengqi Sun. "Mutual information is copula entropy." Tsinghua Science & Technology, 2011.
