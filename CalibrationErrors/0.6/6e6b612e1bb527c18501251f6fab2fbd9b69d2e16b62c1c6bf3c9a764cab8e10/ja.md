```
ECE(binning[, distance = TotalVariation()])
```

与えられた `distance` 関数に対するバイニングアルゴリズムを使用した分類モデルの期待キャリブレーション誤差 (ECE) の推定量。

分類モデルにおいて、予測 $P_{X_i}$ とターゲット $Y_i$ は確率シンプレックス内のベクトルとして識別されます。ECEの推定量は次のように定義されます。

$$
\frac{1}{B} \sum_{i=1}^B d\big(\overline{P}_i, \overline{Y}_i\big),
$$

ここで、$B$ は非空のビンの数、$d$ は距離関数、$\overline{P}_i$ と $\overline{Y}_i$ は $i$ 番目のビンにおける予測の平均ベクトルとターゲットの平均ベクトルです。デフォルトでは、全変動距離が使用されます。

`distance` は次の形式の関数である必要があります。

```julia
distance(pbar::Vector{<:Real}, ybar::Vector{<:Real}).
```

特に、パッケージ [Distances.jl](https://github.com/JuliaStats/Distances.jl) の距離測定がサポートされています。
