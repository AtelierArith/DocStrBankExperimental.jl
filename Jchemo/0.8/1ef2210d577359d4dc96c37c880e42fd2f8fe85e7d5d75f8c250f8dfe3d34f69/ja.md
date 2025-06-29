```
fdasvd(; kwargs...)
fdasvd(X, y, weights; kwargs...)
fdasvd!(X::Matrix, y, weights; kwargs...)
```

階層的判別分析 (FDA)。

  * `X` : Xデータ (n, p)。
  * `y` : yデータ (n) (クラスメンバーシップ)。
  * `weights` : 観測値の重み (n)。タイプ `Weight` でなければなりません (例えば、関数 `mweight` を参照)。

キーワード引数：

  * `nlv` : 判別成分の数。
  * `lb` : リッジ正則化パラメータ "lambda"。 `X` に共線性がある場合に使用できます。
  * `prior` : クラスメンバーシップのための事前確率のタイプ。可能な値は： `:unif` (一様)、 `:prop` (比例)、または各クラスの事前重みを与えるベクトル (ベクトルの場合、`mlev(y)` と同じ順序でソートされている必要があります)。
  * `scal` : ブール値。 `true` の場合、 `X` の各列はその未修正の標準偏差でスケーリングされます。

クラスセンターの行列の重み付きSVD因子分解によるFDA (球面変換後)。この関数は、関数 `fda` と同じ結果を返します。

詳細と例については、関数 `fda` を参照してください。
