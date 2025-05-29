```
updateZ!([rng::AbstractRNG], Z::AbstractVector, alg::OnIPSA, X::AbstractVector; [kwargs...])
```

Update inducing points `Z` with data `X` and algorithm `alg`. Requires additional keyword arguments for some algorithms. Also see `InducingPoints`.
