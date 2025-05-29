```
entropy(logᵦ, img)
entropy(img; [kind=:shannon])
```

Compute the entropy of a grayscale image defined as `-sum(p.*logᵦ(p))`. The base β of the logarithm (a.k.a. entropy unit) is one of the following:

  * `:shannon` (log base 2, default), or use logᵦ = log2
  * `:nat` (log base e), or use logᵦ = log
  * `:hartley` (log base 10), or use logᵦ = log10
