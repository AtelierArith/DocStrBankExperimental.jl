```
energy(f, x, y::Int; agg=mean)
```

Computes the energy for conditional samples $x \sim p_{\theta}(x|y)$: $E(x)=- f_{\theta}(x)[y]$.
