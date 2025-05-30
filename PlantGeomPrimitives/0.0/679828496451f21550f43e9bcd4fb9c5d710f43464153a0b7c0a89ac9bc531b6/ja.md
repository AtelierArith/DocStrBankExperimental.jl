```
SolidCone(;length = 1.0, width = 1.0, height = 1.0, n = 40)
```

指定された寸法のソリッドコーンを作成します。寸法は`length`、`width`、`height`によって与えられ、`n`個の三角形に離散化されます（偶数でなければなりません）および標準の位置と向きです。

# 引数

  * `length = 1.0`: コーンの長さ（基底と頂点の間の距離）。
  * `width = 1.0`: コーンの基底の幅。
  * `height = 1.0`: コーンの基底の高さ。
  * `n = 40`: メッシュに使用される三角形の数。

# 例

```jldoctest
julia> SolidCone(;length = 1.0, width = 1.0, height = 1.0, n = 40);
```
