```
G
G(D)
```

User interface for [`GMatrix`](@ref), as defined by Aitchison.

`G` is an `D` by `D` matrix that can be defined as

`G[i, j] = I[i, j] - J[i, j] / D`

## Examples

```
julia> G(3)
julia> G*v
julia> v'*G
```
