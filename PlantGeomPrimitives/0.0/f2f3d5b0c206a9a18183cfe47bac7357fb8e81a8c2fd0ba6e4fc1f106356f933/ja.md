```
HollowCylinder(;length = 1.0, width = 1.0, height = 1.0, n = 40)
```

`length`、`width`、`height` で指定された寸法の中空円柱を作成し、`n` 三角形に離散化します（偶数でなければなりません）および標準の位置と向き。

# 引数

  * `length = 1.0`: 円柱の長さ（基底間の距離）。
  * `width = 1.0`: 円柱の基底の幅。
  * `height = 1.0`: 円柱の基底の高さ。
  * `n = 40`: 円柱を離散化する三角形の数。

# 例

```jldoctest
julia> HollowCylinder(;length = 1.0, width = 1.0, height = 1.0, n = 40);
```
