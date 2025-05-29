```
mdop_embedding(s::Vector; kwargs...) → Y, τ_vals, ts_vals, FNNs, βS
```

MDOP（「プロジェクション上の導関数を最大化する」ための略称）は、Chetan Nichkawdeの論文に基づいて、時系列または時系列のセット（`StateSpaceSet`）を適切に埋め込むための統一アプローチです[^Nichkawde2013]。

## キーワード引数

  * `τs= 0:50`: 可能な遅延値 `τs`。各 `τs` に対して β統計量が計算されます。
  * `w::Int = 1`: タイムスライドウィンドウ（点に近いインデックス `w` の時間的隣接点で、真の隣接点から除外されます）。`w=0` は点自体のみを除外し、時間的隣接点は除外しません。
  * `fnn_thres::Real= 0.05`: アルゴリズムが終了し、埋め込み手順を停止するために十分に小さな偽の近接隣接点の割合を定義する閾値（`0 ≤ fnn_thres < 1`）。
  * `r::Real = 2`: 埋め込み次元を増加させるときに、最も近い隣接点間の距離の許容される相対的増加の閾値。
  * `max_num_of_cycles = 50`: アルゴリズムは、そのサイクル数の後に停止します。

## 説明

このメソッドは反復的に動作し、最終的な埋め込み `Y` を徐々に構築します。[`beta_statistic`](@ref) に基づいて、アルゴリズムは各埋め込みサイクルの最適な遅延値 `τ` を `β` のグローバル最大値として選択します。多変量埋め込みの場合、すなわち時系列のセット（`s::StateSpaceSet`）を埋め込む場合、最適な遅延値 `τ` は、考慮された各時系列のすべての最大値の中から最大のものとして選ばれます。考慮される遅延値の範囲は `τs` で決定され、最も近い隣接点の検索にはタイラーウィンドウ `w` を考慮します。

各埋め込みサイクルの後、FNN統計量 `FNNs` [^Hegger1999][^Kennel1992] がチェックされ、この統計量が閾値 `fnn_thres` を下回ると、アルゴリズムは終了します。メソッドの実用性を高めるために、FNN統計量 `FNNs` が増加した場合にもアルゴリズムは終了します。

最終的な埋め込みは `Y` として返されます。各埋め込みサイクルのために選択された遅延値は `τ_vals` に保存され、対応する遅延値に対して選択された時系列インデックスは `ts_vals` に保存されます。`βS, FNNs` は明確さと二重確認のために返されます。なぜなら、これらはどうせ計算されるからです。多変量埋め込みの場合、`βS` は各埋め込みサイクルで利用可能なすべての時系列のすべての `β`-統計量を保存します。埋め込みサイクル 'k' で実際に使用された `β`-統計量を二重確認するには、単に `βS[k][:,ts_vals[k+1]]` を使用します。

[^Nichkawde2013]: Nichkawde, Chetan (2013). [Optimal state-space reconstruction using derivatives on projected manifold. Physical Review E 87, 022905](https://doi.org/10.1103/PhysRevE.87.022905).

[^Hegger1999]: Hegger, Rainer and Kantz, Holger (1999). [Improved false nearest neighbor method to detect determinism in time series data. Physical Review E 60, 4970](https://doi.org/10.1103/PhysRevE.60.4970).

[^Kennel1992]: Kennel, M. B., Brown, R., Abarbanel, H. D. I. (1992). [Determining embedding dimension for state-space reconstruction using a geometrical construction. Phys. Rev. A 45, 3403](https://doi.org/10.1103/PhysRevA.45.3403).
