```
markovparam(sys, n)
```

Compute the `n`th markov parameter of discrete-time state-space system `sys`. This is defined as the following:

`h(0) = D`

`h(n) = C*A^(n-1)*B`
