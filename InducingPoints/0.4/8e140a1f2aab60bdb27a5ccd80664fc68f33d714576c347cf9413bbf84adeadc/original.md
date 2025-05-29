```
updateZ!([rng::AbstractRNG], Z::AbstractVector, alg::OIPS, X::AbstractVector; kernel::Kernel)
```

Update inducing points `Z` with data `X` and the OnlineIPSelection algorithm. Requires the `kernel` as an  additional keyword argument. 
