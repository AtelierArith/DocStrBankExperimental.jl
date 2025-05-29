```
predict_point!(predictions, i, source_values, u, w, dists, dim)
```

収束交差マッピングアルゴリズムの予測部分。

## アルゴリズム

時間インデックス `i` の `target` ポイントの遅延埋め込みにおける点を考えます。その最近傍の時間インデックスを $t_1, t_2, \ldots, t_{dim+1}$ とします。それらの時間インデックスにおける `source` のスカラー値を $y_1, y_2, \ldots, y_{dim+1}$ とします。

`i` 番目のポイントからその最近傍までの距離 `distances` $d_1, d_2, \ldots, d_{dim+1}$ を考慮し、交差マッピングアルゴリズムから重み `w` を計算します（[Sugihara et al, 2012; 補足資料, ページ 4](http://science.sciencemag.org/content/sci/suppl/2012/09/19/science.1227079.DC1/Sugihara.SM.pdf)）。重み `w` と係数 `u` は事前に確保されたベクトルに格納されます。

`source` タイムシリーズにおける時間インデックス `i` の観測値の予測を $\hat{y}(i)$ と呼び、次のように計算されます。

$$
\hat{y}(i) = \sum_{j=1}^{dim+1} w_j y_j.
$$

予測値 $\hat{y}(i)$ は、事前に確保されたベクトル `predictions` の位置 `i` に格納されます。

## 引数

  * **`predictions`**: `source` シリーズのスカラー値の予測を格納するための事前に確保されたベクトル。
  * **`i`**: 予測される `source` シリーズのポイントの時間インデックス。予測は `predictions[i]` に格納されます。
  * **`source_values`**: $t_1, t_2, \ldots, t_{dim + 1}$ を時間インデックスとし、遅延埋め込みポイントの時間インデックス `i` に対する最近傍の時間インデックスとします。`source_values` には、それらの時間インデックスにおける `source` シリーズのスカラー値が含まれます。
  * **`u`**: 交差マッピングアルゴリズムで重みを計算するための正規化係数を保持する長さ `dim + 1` の事前に確保されたベクトル。
  * **`w`**: 交差マッピングアルゴリズムのために計算された重みを保持する長さ `dim + 1` の事前に確保されたベクトル。
  * **`dists`**: 時間インデックス `i` の遅延埋め込みポイントからその `dim + 1` の最近傍までの距離で、距離が増加する順に並んでいます。
  * **`dim`**: 遅延埋め込みの次元。

## 参考文献

Sugihara, George, et al. "Detecting causality in complex ecosystems." Science (2012): 1227079. [http://science.sciencemag.org/content/early/2012/09/19/science.1227079](http://science.sciencemag.org/content/early/2012/09/19/science.1227079)
