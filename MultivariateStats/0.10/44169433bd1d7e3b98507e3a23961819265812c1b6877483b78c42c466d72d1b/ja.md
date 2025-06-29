```
fit(MulticlassLDA, X, y; ...)
```

与えられたデータセット `X` と対応するラベル `y` に対して、`nc` クラス数の多クラス LDA を実行します。

この関数は、[`MulticlassLDA`](@ref) のインスタンスとして結果の多クラス LDA モデルを返します。

*パラメータ*

  * `X`:   入力サンプルの行列、サイズは `(d, n)`。`X` の各列は観測値です。
  * `y`:   クラスラベルのベクトル、長さは `n`。

**キーワード引数**

  * `method`: メソッドの選択:

      * `:gevd`: 一般化固有値分解に基づく (*デフォルト*)。
      * `:whiten`: 最初に `Sw` からホワイトニング変換を導出し、その後、ホワイトニングされた `Sb` の固有値分解に基づいて問題を解決します。
  * `outdim`: 出力次元、すなわち変換空間の次元 `min(d, nc-1)`
  * `regcoef`: 正則化係数 (*デフォルト:* `1.0e-6`)。正の値 `regcoef * eigmax(Sw)` が `Sw` の対角に追加され、数値的安定性が向上します。
  * `covestimator_between`: クラス間共分散のカスタム共分散推定器 (*デフォルト:* `SimpleCovariance()`)。共分散行列は `cov(covestimator_between, #=data=#; dims=2, mean=zeros(#=...=#))` として計算されます。その他のパッケージで利用可能なカスタム共分散推定器は、観測値よりも特徴が多いデータに対してより堅牢な判別をもたらす可能性があります。
  * `covestimator_within`: クラス内共分散のカスタム共分散推定器 (*デフォルト:* `SimpleCovariance()`)。共分散行列は `cov(covestimator_within, #=data=#; dims=2, mean=zeros(nc))` として計算されます。その他のパッケージで利用可能なカスタム共分散推定器は、観測値よりも特徴が多いデータに対してより堅牢な判別をもたらす可能性があります。

**注意:**

結果の射影行列 $P$ は次の条件を満たします:

$$
\mathbf{P}^T (\mathbf{S}_w + \kappa \mathbf{I}) \mathbf{P} = \mathbf{I}
$$

ここで、$\kappa$ は `regcoef * eigmax(Sw)` に等しいです。$\mathbf{P}$ の列は、対応する一般化固有値の降順に配置されています。

[`MulticlassLDA`](@ref) は現在、$\mathbf{S}_w^*$ および $\mathbf{S}_b^*$ を使用した正規化バージョンをサポートしていないことに注意してください（[`SubspaceLDA`](@ref) を参照）。
