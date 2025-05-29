```
HollowCone(;length = 1.0, width = 1.0, height = 1.0, n = 20)
```

`length`、`width`、`height` で指定された寸法の中空円錐を作成し、`n` 個の三角形に離散化します（偶数でなければなりません）および標準の位置と向き。

# 引数

  * `length = 1.0`: 円錐の長さ（基底と頂点の間の距離）。
  * `width = 1.0`: 円錐の基底の幅。
  * `height = 1.0`: 円錐の基底の高さ。
  * `n = 20`: メッシュに使用される三角形の数。

# 例

```jldoctest
julia> HollowCone(;length = 1.0, width = 1.0, height = 1.0, n = 20);
```
