```
rlocusplot(P::LTISystem, K)
```

Computes and plots the root locus of the SISO LTISystem P with a negative feedback loop and feedback gains `K`, if `K` is not provided, range(1e-6,stop=500,length=10000) is used. If `OrdinaryDiffEq.jl` is installed and loaded by the user (`using OrdinaryDiffEq`), `rlocusplot` will use an adaptive step-size algorithm to select values of `K`. A scalar `Kmax` can then be given as second argument.
