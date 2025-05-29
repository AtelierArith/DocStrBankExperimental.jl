```
SolidCylinder(;length = 1.0, width = 1.0, height = 1.0, n = 80)
```

指定された寸法のソリッドシリンダーを作成します。寸法は `length`、`width`、`height` で、`n` 三角形に離散化されます（偶数でなければなりません）および標準の位置と向きです。

# 引数

  * `length = 1.0`: シリンダーの長さ（基底間の距離）。
  * `width = 1.0`: シリンダーの基底の幅。
  * `height = 1.0`: シリンダーの基底の高さ。
  * `n = 80`: シリンダーを離散化する三角形の数。

# 例

```jldoctest
julia> SolidCylinder(;length = 1.0, width = 1.0, height = 1.0, n = 80);
```
