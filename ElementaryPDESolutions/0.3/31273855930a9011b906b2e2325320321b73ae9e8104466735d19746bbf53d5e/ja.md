```
solve_laplace(Q::Polynomial)
```

ポリノミアル `P` を返します。これは `ΔP = Q` を満たします。`Q` は同次である必要があります。

# 例

```jldoctest
julia> Q = Polynomial((1,0)=>1.0)
x

julia> P = solve_laplace(Q)
0.125xy² + 0.125x³
```
