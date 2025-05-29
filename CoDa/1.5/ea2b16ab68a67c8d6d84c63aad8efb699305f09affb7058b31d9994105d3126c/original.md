```
H
H(d)
```

User interface for [`HMatrix`](@ref), as defined by Aitchison.

`H` is a `d` by `d` matrix that can be defined as

`H[i, j] = I[i, j] + J[i, j]`

## Examples

```
julia> H(3)
julia> H*v
julia> v'*H
```
