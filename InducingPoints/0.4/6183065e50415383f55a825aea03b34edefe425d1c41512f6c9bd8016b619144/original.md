```
 inducingpoints([rng::AbstractRNG], alg::RandomSubset, X::AbstractVector; [weights::Vector=nothing])
 inducingpoints([rng::AbstractRNG], alg::RandomSubset, X::AbstractMatrix; obsdim=1, [weights::Vector=nothing])
```

Select inducing points by taking a Random Subset. Optionally accepts a weight vector for the inputs `X`.
