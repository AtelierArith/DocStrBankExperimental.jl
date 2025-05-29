```
SolidCone(;length = 1.0, width = 1.0, height = 1.0, n = 40)
```

与えられた寸法 `length`、`width`、`height` に基づいてソリッドコーンを作成し、`n` 三角形（偶数でなければならない）に離散化し、標準の位置と向きを持ちます。

# 引数

  * `length = 1.0`: コーンの長さ（基底と頂点の間の距離）。
  * `width = 1.0`: コーンの基底の幅。
  * `height = 1.0`: コーンの基底の高さ。
  * `n = 40`: メッシュに使用される三角形の数。

# 例

```jldoctest
julia> SolidCone(;length = 1.0, width = 1.0, height = 1.0, n = 40);
```
