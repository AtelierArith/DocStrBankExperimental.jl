```
getrowrange(n, idx)
```

Get the row range from a matrix with `n` rows that corresponds to `idx` from a quadtree.

# Arguments

  * `n::Integer`: Number of rows in matrix.
  * `idx::T where T<:Integer`: Index from a quadtree corresponding to the matrix.

# Returns

`::UnitRange{Int64}`: Row range in matrix that corresponds to `idx`.

# Examples

```@repl
using WaveletsExt

x = randn(8,8)
tree = maketree(x, 3, :full)
getrowrange(8,3)            # 1:4
```

**See also:** [`Wavelets.Util.maketree`](@ref), [`getcolrange`](@ref)
