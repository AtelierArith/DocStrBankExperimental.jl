```
optimal_traditional_de(s, method = "afnn", dmethod = "mi_min"; kwargs...) → 𝒟, τ, E
```

与えられた時系列 `s` の最適な遅延埋め込み `𝒟` を生成するには、まず与えられた `dmethod` を使用して最適（かつ一定の）遅延時間を [`estimate_delay`](@ref) で見つけ、その後、各次元 `d ∈ 1:dmax` に対して適切な統計量を計算することによって最適な埋め込み次元を見つけます。埋め込み `𝒟`、最適な遅延時間 `τ`（最適な埋め込み次元 `d` は `size(𝒟, 2)` です）、および最適な `d` を推定するために使用された実際の統計量 `E` を返します。

`E` は埋め込み次元の関数であり、1 から `dmax` までの範囲です。

次元を推定するために `E` を計算するには、次の `method` を使用します：

  * `"afnn"`（デフォルト）は、Cao の "Averaged False Nearest Neighbors" メソッド[^Cao1997] で、最近接近傍間の距離の比率を提供します。
  * `"ifnn"` は、Hegger & Kantz の "Improved False Nearest Neighbors"[^Hegger1999] で、偽の最近接近傍の割合を提供します。
  * `"fnn"` は、Kennel の "False Nearest Neighbors" メソッド[^Kennel1992] で、次元が増加する際に "最近接近傍" でなくなる点の数を提供します。
  * `"f1nn"` は、Krakovská の "False First Nearest Neighbors" メソッド[^Krakovská2015] で、次元が増加する際に "最近接近傍" でなくなる点のペアの比率を提供します。

詳細については、各メソッドを参照してください： [`delay_afnn`](@ref)、[`delay_ifnn`](@ref)、[`delay_fnn`](@ref)、[`delay_f1nn`](@ref)。特別なキーワード `` は、統計量を計算する必要がある可能な埋め込み次元を示します。

!!! warn "自動化された方法に注意"
    この方法は自動化されていますが、結果に**本当に確信がある**場合は、統計量を直接計算し、その値を次元に対してプロットするべきです。


## キーワード

キーワード

```
τs = 1:100, dmax = 10
```

は、最適な埋め込みを計算する際に考慮すべき遅延時間と埋め込み次元 `ds ∈ 1:dmax` を示します。残りのすべてのキーワードは、低レベルの関数に伝播されます：

```
fnn_thres::Real = 0.05, slope_thres::Real= 0.2, w::Int=1,
rtol=10.0, atol=2.0, τs = 1:100, metric = Euclidean(), r::Real=2.0,
stoch_thres = 0.1
```

## 説明

与えられた遅延時間を `dmethod` から得た最適な埋め込み次元を次のように推定します：Cao のメソッドでは、`E₁` 統計量（"afnn" からの出力）の傾きが閾値 `slope_thres`（デフォルトは .05）を下回り、対応する確率的テストが偽である場合、すなわち `E₂` 統計量の最初の値が `< 1 - stoch_thres` であるときに最適な次元に達します。

他のすべてのメソッドでは、対応する FNN 統計量（"ifnn"、"fnn" または "f1nn" からの出力）が fnn 閾値 `fnn_thres`（デフォルトは .05）を下回り、かつ統計量の傾きが閾値 `slope_thres` を下回るときに最適な埋め込み次元を返します。ノイズが混入した時系列では、ノイズレベルに応じて `fnn_thres` を調整する必要があるかもしれません。

比較については、ファイル `test/compare_different_dimension_estimations.jl` も参照してください。

[^Cao1997]: Liangyue Cao, [Physica D, pp. 43-50 (1997)](https://www.sciencedirect.com/science/article/pii/S0167278997001188?via%3Dihub)

[^Kennel1992]: M. Kennel *et al.*, [Phys. Review A **45**(6), (1992)](https://journals.aps.org/pra/abstract/10.1103/PhysRevA.45.3403).

[^Krakovská2015]: Anna Krakovská *et al.*, [J. Complex Sys. 932750 (2015)](https://doi.org/10.1155/2015/932750)

[^Hegger1999]: Hegger & Kantz, [Improved false nearest neighbor method to detect determinism in time series data. Physical Review E 60, 4970](https://doi.org/10.1103/PhysRevE.60.4970).

```
