```
SolidFrustum(;length = 1.0, width = 1.0, height = 1.0, ratio = 1.0, n = 40)
```

指定された寸法のソリッドフラスタムを作成します。寸法は`length`、`width`、`height`によって与えられ、`n`個の三角形に離散化され、標準の位置と向きになります。

# 引数

  * `length = 1.0`: フラスタムの長さ（基底間の距離）。
  * `width = 1.0`: フラスタムの基底の幅。
  * `height = 1.0`: フラスタムの基底の高さ。
  * `ratio = 1.0`: 上部と下部の基底半径の比率。
  * `n = 40`: フラスタムを離散化する三角形の数。

# 例

```jldoctest
julia> SolidFrustum(;length = 1.0, width = 1.0, height = 1.0, n = 40, ratio = 0.5);
```
