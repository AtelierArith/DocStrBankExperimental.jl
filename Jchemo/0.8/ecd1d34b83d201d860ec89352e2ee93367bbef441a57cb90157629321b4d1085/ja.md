```
list(Q, n::Integer)
```

ベクター `{Q}(undef, n)` を作成します。

`isassigned(object, i)` を使用して、セル i が空であるかどうかを確認できます。

## 例

```julia
using Jchemo

list(Float64, 5)
list(Array{Float64}, 5)
list(Matrix{Int}, 5)
```
