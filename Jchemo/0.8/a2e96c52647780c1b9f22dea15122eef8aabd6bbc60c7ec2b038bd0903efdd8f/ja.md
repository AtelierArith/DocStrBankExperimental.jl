```
rrchol(; kwargs...)
rrchol(X, Y; kwargs...)
rrchol(X, Y, weights::Weight; kwargs...)
rrchol!(X::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

ノルマル方程式とコレスキー分解を使用したリッジ回帰（RR）。

  * `X` : Xデータ (n, p)。
  * `Y` : Yデータ (n, q)。
  * `weights` : 観測値の重み (n)。 `Weight` 型でなければなりません（例えば、関数 `mweight` を参照）。

キーワード引数：

  * `lb` : リッジ正則化パラメータ "lambda"。
  * `scal` : ブール値。 `true` の場合、`X` の各列はその未修正標準偏差でスケーリングされます。

例については関数 `rr` を参照してください。

## 参考文献

Cule, E., De Iorio, M., 2012. リッジ回帰におけるリッジパラメータの選択を導く半自動的手法。 arXiv:1205.0686.

Hastie, T., Tibshirani, R., 2004. 表現配列のための効率的な二次正則化。 Biostatistics 5, 329-340.  https://doi.org/10.1093/biostatistics/kxh010

Hastie, T., Tibshirani, R., Friedman, J., 2009. 統計学習の要素：データマイニング、推論、予測、第2版。 Springer, New York.

Hoerl, A.E., Kennard, R.W., 1970. リッジ回帰：非直交問題のためのバイアス推定。 Technometrics 12, 55-67.  https://doi.org/10.1080/00401706.1970.10488634 ```
