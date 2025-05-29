```
getoffset(TDB, TT, second, fraction[, eop])
```

現在のエポック（J2000以降の`second`と`fraction`）における[`TDB`](@ref)と[`TT`](@ref)のオフセットを、地球上の観測者に対して秒単位で返します。

### 引数

  * `second`, `fraction`: 現在のエポック
  * `elong`: 経度（東が正、ラジアン）
  * `u`: 地球の回転軸からの距離（km）
  * `v`: 赤道面の北側の距離（km）

# 例

```jldoctest; setup = :(using AstroTime)
julia> getoffset(TDB, TT, 0, 0.0, π, 6371.0, 0.0)
9.928419814106208e-5
```

### 参考文献

  * [ERFA](https://github.com/liberfa/erfa/blob/master/src/dtdb.c)
