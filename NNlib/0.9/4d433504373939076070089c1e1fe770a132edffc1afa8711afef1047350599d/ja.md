```
lpnormpool(x, p::Real, k::NTuple{N, Integer}; pad=0, stride=k)
```

入力テンソル `x` に対して Lp ノルム `p` の値とウィンドウサイズ `k` を用いて Lp プール操作を実行します。これは pytorch での LPPool としても知られています。このプーリング演算子は [Learned-Norm Pooling for Deep Feedforward and Recurrent Neural Networks](https://arxiv.org/abs/1311.1780) からのものです。

引数:

  * `x` と `k`: `ndim(x) ∈ 3:5` を期待し、常に `length(k) == ndim(x) - 2` である必要があります。
  * `p` は `0 < p < Inf` に制限されています。
  * `pad`: 詳細については [`pad_zeros`](@ref) を参照してください。
  * `stride`: `k` と同じ長さのタプル、またはすべての方向に対して1つの整数です。デフォルトは `k` です。

サイズ `k` のウィンドウ内のすべての要素 `x` に対して、lpnormpool は `(∑ᵢ xᵢ^p)^(1 / p)` を出力の要素として計算します。

したがって `lpnormpool(x, 1, k) ./ prod(k) ≈ meanpool(x, k)` および `lpnormpool(x, 2, k).^2 ./ prod(k) ≈ meanpool(x.^2, k)` となります。
