```
IDWInterpolator(factors; leafsize=10, k=8, power=1, reg=0, conf_dist=1e-12)
```

シェパード逆距離加重補間スキームを使用してメッシュの解像度を上げます。

`factors`は「ズーム」のレベルを表し、サイズが`(10, 10)`の入力メッシュに対して`(2, 2)`のファクターを指定すると、出力サイズは`(20, 20)`になります。整数のみが提供された場合、それはすべての軸のファクターとして使用されます。

補間器は、いくつかの追加パラメータで呼び出すことができます：

  * `leaf_size`は、ツリーをさらに分割するのを停止するポイントの数を決定します。
  * `k`は考慮される最近傍の数です。
  * `power`は重み付け因子の距離の指数です。
  * `reg`は分母の重み付け因子のオフセットです。
  * `conf_dist`は、2つのポイントが同じポイントと見なされる距離です。

# 例

```jldoctest
julia> IDWInterpolator(2, k=2)([1 0; 0 1])
4×4 Matrix{Float64}:
 1.0   0.75      0.25      0.0
 0.75  0.690983  0.309017  0.25
 0.25  0.309017  0.690983  0.75
 0.0   0.25      0.75      1.0

julia> IDWInterpolator(3, 1; k=2, power=4)([1 0; 0 1])
6×2 Matrix{Float64}:
 1.0        0.0
 1.0        0.0
 0.941176   0.0588235
 0.0588235  0.941176
 0.0        1.0
 0.0        1.0
```
