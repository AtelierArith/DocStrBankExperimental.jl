```
getcolrange(n, idx)
```

Get the column range from a matrix with `n` columns that corresponds to `idx` from a quadtree.

# Arguments

  * `n::Integer`: Number of columns in matrix.
  * `idx::T where T<:Integer`: Index from a quadtree corresponding to the matrix.

# Returns

`::UnitRange{Int64}`: Column range in matrix that corresponds to `idx`.

# Examples

```@repl
using WaveletsExt

x = randn(8,8)
tree = maketree(x, 3, :full)
getcolrange(8,3)            # 5:8
```

**See also:** [`Wavelets.Util.maketree`](@ref), [`getrowrange`](@ref)
