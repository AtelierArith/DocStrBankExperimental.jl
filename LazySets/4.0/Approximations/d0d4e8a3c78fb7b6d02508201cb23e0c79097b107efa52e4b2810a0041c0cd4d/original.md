```
overapproximate(X::Intersection{N, <:AbstractZonotope, <:Hyperplane},
                ::Type{<:Zonotope})
```

Overapproximate the intersection of a zonotopic set and a hyperplane with a zonotope.

### Input

  * `X`        – intersection of a zonotopic set and a hyperplane
  * `Zonotope` – target set type

### Output

A zonotope overapproximating the intersection.

### Algorithm

This method implements [MaigaRTC14; Algorithm 3](@citet).
