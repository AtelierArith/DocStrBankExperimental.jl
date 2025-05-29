```
x = reject(P,w,N,Pmax)
```

Generate `x` distributed according to a probability distribution by rejection sampling over a finite window.

`P`: probability distribution, normalized to 1.

`w=[w1,w2]`: window for sampling `x`.

`N`: number of samples.

`Pmax`: numerical upper bound for `P`: `Pmax ≧ max(P(w))`.
