```
SnpLinAlg{T}(s; model=ADDITIVE_MODEL, center=false, scale=false, impute=true)
```

Pad a `SnpArray` with some parameters for linear algebera operation.

# Arguments

  * s: a `SnpArray`.
  * model: one of `ADDITIVE_MODEL`(default), `DOMINANT_MODEL`, `RECESSIVE_MODEL`.
  * center: whether to center (default: false).
  * scale: whether to scale to standard deviation 1 (default: false).
  * impute: whether to impute missing value with column mean (default: true).
