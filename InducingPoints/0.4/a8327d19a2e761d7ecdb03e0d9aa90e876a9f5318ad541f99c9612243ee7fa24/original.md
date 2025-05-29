```
 inducingpoints([rng::AbstractRNG], alg::OIPS, X::AbstractVector; kernel::Kernel)
 inducingpoints([rng::AbstractRNG], alg::OIPS, X::AbstractMatrix; obsdim=1, kernel::Kernel)
```

Select inducing points according using Online Inducing Points Selection. Requires as additional keyword argument the `kernel`.
