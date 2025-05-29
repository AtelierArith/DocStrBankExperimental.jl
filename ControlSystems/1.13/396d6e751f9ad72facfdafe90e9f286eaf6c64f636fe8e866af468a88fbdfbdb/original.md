```
roots, Z, K = rlocus(P::LTISystem, K = 500)
```

Compute the root locus of the SISO LTISystem `P` with a negative feedback loop and feedback gains between 0 and `K`. `rlocus` will use an adaptive step-size algorithm to determine the values of the feedback gains used to generate the plot.

`roots` is a complex matrix containing the poles trajectories of the closed-loop `1+k⋅G(s)` as a function of `k`, `Z` contains the zeros of the open-loop system `G(s)` and `K` the values of the feedback gain.
