```
JacobiWeight(β,α,s::Space)
```

weights a space `s` by a Jacobi weight, which on `-1..1` is `(1+x)^β*(1-x)^α`. For other domains, the weight is inferred by mapping to `-1..1`.
