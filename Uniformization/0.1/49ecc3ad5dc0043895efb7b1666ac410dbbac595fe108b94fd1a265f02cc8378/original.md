```
uniformize(Q, p0, k=2^10, t=0.0,
           method::Function=erlangization, args...)
```

Approximate 𝐩(t) = exp(t𝐐)𝐩(0) using uniformization. The parameter k controls the rate of transitions occurring in the approximated process. Higher k leads to a better approximation. Returns a (normalized) distribution over the states at time 𝑡.

Uses Erlangization/external uniformization by default because it seems to be the most robust with stiff problems.
