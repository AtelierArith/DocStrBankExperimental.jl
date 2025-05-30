```
HollowFrustum(;length = 1.0, width = 1.0, height = 1.0, ratio = 1.0, n = 40)
```

`length`、`width`、`height` で指定された寸法の中空のフラスコを作成し、`n` 個の三角形に離散化します（偶数でなければなりません）および標準の位置と向き。

# 引数

  * `length = 1.0`: フラスコの長さ（基底間の距離）。
  * `width = 1.0`: フラスコの基底の幅。
  * `height = 1.0`: フラスコの基底の高さ。
  * `ratio = 1.0`: 上部と下部の基底半径の比率。
  * `n = 40`: フラスコを離散化する三角形の数。

# 例

```jldoctest
julia> HollowFrustum(;length = 1.0, width = 1.0, height = 1.0, n = 40, ratio = 0.5);
```
