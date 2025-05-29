```
solve_helmholtz(Q::Polynomial;k=1)
```

唯一の多項式 `P` を返します。これは `ΔP + k²P = Q` を満たします。

# 例

```jldoctest
julia> Q = Polynomial((1,2)=>1)
xy²

julia> P = solve_helmholtz(Q, k=1)
-2.0x + xy²
```
