```
 inducingpoints([rng::AbstractRNG], alg::AIPSA, X::AbstractVector; [kwargs...])
 inducingpoints([rng::AbstractRNG], alg::AIPSA, X::AbstractMatrix; obsdim=1, [kwargs...])
```

Select inducing points according to the algorithm `alg`. For some algorithms, additional keyword arguments are required. 
