```
overapproximate(r::Rectification{N, <:AbstractZonotope},
                ::Type{<:Zonotope}) where {N}
```

Overapproximate the rectification of a zonotopic set with a zonotope.

### Input

  * `r`        – lazy rectification of a zonotopic set
  * `Zonotope` – target set type

### Output

A zonotope overapproximation of the set obtained by rectifying `Z`.

### Algorithm

This method implements [SinghGMPV18; Theorem 3.1](@citet).
