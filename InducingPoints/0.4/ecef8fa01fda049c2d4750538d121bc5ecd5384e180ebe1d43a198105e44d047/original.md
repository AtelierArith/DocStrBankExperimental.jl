```
 inducingpoints([rng::AbstractRNG], alg::SeqDPP, X::AbstractVector; kernel::Kernel)
 inducingpoints([rng::AbstractRNG], alg::SeqDPP, X::AbstractMatrix; obsdim=1, kernel::Kernel)
```

Select inducing points according using Sequential Determinantal Point Processes. Requires passing a `kernel::Kernel` as a keyword argument.
