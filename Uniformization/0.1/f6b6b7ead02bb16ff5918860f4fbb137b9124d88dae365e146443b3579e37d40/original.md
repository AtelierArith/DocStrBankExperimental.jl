```
standard_uniformization(Q, k=2^10, t=0.0, ϵ=10e-9; p0)
```

Approximate 𝐩(t) = exp(t𝐐)𝐩(0) using standard uniformization with left and right truncation of the Poisson distribution used to approximate the number of jumps up to time t. The rules for choosing the left and right truncation points are based on Reibman & Trivedi (1988, Computers & Operations Research).

Note that this computes 𝐩(t) on the fly; it does not return the matrix 𝐑(t) as erlangization() and discrete*observation*() do.
