```
solve_bilaplace(Q::Polynomial)
```

`Δ²P = Q` の多項式解を計算します。`Q` は同次である必要があります。

# 例

```jldoctest
julia> Q = Polynomial((1,0)=>1)
x

julia> P = solve_bilaplace(Q)
1//192x⁵ + 1//96x³y² + 1//192xy⁴
```
