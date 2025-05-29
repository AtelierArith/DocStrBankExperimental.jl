```
F
F(d)
```

User interface for [`FMatrix`](@ref), as defined by Aitchison.

`F` is a `d` by `D` matrix that can be defined as

`F[i, j] = 1`, if `i==j`

`F[i, j] = -1`, if `j==D`

`F[i, j] = 0`, otherwise

## Examples

```
julia> F(3)
julia> F*v
julia> v'*F
```
