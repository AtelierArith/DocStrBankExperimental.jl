```
overapproximate(Z::AbstractZonotope, ::Type{<:HParallelotope},
                [indices]=1:dim(Z))
```

Overapproximate a zonotopic set with a parallelotope in constraint representation.

### Input

  * `Z`              – zonotopic set
  * `HParallelotope` – target set type
  * `indices`        – (optional; default: `1:dim(Z)`) generator indices selected                      when constructing the parallelotope

### Output

An overapproximation of the given zonotopic set using a parallelotope.

### Algorithm

The algorithm is based on Proposition 8 discussed in [AlthoffSB10; Section 5](@citet).
