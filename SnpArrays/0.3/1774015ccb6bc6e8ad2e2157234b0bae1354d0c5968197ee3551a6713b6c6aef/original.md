```
SnpBitMatrix{T}(s; model=ADDITIVE_MODEL, center=false, scale=false)
```

Store an `AbstractSnpArray` `s` as two `BitMatrix`es to simplify linear algebra.

# Arguments

  * s: an `AbstractSnpArray`.
  * model: one of `ADDITIVE_MODEL`(default), `DOMINANT_MODEL`, `RECESSIVE_MODEL`.
  * center: whether to center (default: false).
  * scale: whether to scale to standard deviation 1 (default: false).
