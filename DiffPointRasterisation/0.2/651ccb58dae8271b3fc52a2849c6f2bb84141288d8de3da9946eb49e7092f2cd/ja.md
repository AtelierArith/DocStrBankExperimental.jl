```
raster(grid_size, points, rotation, translation, [background, out_weight])
```

ポイントを `grid_size` サイズの Nd-array に (多重) 線形補間します。

`points` が配列に補間される前に、各ポイント $p$ はまず次のように変換されます。

$$
\hat{p} = R p + t
$$

ここで `rotation` は $R$、`translation` は $t$ です。

N次元のハイパーキューブに入るポイント $\hat{p}$ は、出力配列に補間されます。このハイパーキューブのエッジは各次元で (-1, 1) から広がっています。

各ポイントの総重量 (`out_weight * point_weight`) は、出力配列の 2^N の最近接ピクセル/ボクセルに分配されます（ボクセル中心とポイント $\hat{p}$ の座標の近さに応じて） N-線形補間を介して行われます。

# 引数

  * `grid_size`: 出力次元を定義する整数のタプル
  * `points::AbstractVector{<:AbstractVector}`: ポイントを表す同じ長さのベクトルのベクトル
  * `rotation`: 単一の行列（のようなオブジェクト）またはそのようなベクトルで、`points` をラスタライズする前に線形変換します。
  * `translation`: 単一のベクトルまたはそのようなベクトルで、`rotation` の後に `points` を移動します。`rotation` に投影が含まれている場合、`translation` は `rotation * points[i]` と同じ長さである必要があります。
  * `background`: 単一の数またはそのようなベクトル。
  * `out_weight`: 単一の数またはそのようなベクトル（画像ごとに1つ）。
  * `point_weight`: 数のベクトル（ポイントごとに1つ）。

`rotation`、`translation`、`background` および `out_weight` は、追加の "バッチ" 次元を持つことができます（単一のパラメータのベクトルとして提供することによって）。これらのベクトルの長さは、4つの引数すべてで同じでなければなりません。この場合、出力配列は次元 +1 を持ち、バッチ内の要素の数に対応する追加の軸が最後の位置に追加されます。詳細については、[Raster a single point cloud to a batch of poses](@ref) を参照してください。

参照: [`raster!`](@ref)
