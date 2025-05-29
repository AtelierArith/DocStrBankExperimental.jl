```
PauliVec
```

パウリ行列の固有ベクトルを保持する定数です。インデックス 1、2、および 3 はそれぞれ $σ_x$、$σ_y$ および $σ_z$ の固有ベクトルに対応します。

# 例

```julia-repl
julia> σx*PauliVec[1][1] == PauliVec[1][1]
true
```
