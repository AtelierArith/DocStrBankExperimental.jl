```
crossvalidation(x, monitoredfit; ...)
```

k分割交差検証を実行します。与えられたものは次の通りです。

  * データセット `x` と
  * `monitoredfit`: モデルを適合させ評価する関数。引数として次を受け入れなければなりません：

      * トレーニングデータセット
      * 評価データを含む `DataDict`。

`monitoredfit` 関数への呼び出しの戻り値は `vcat` で連結されます。`monitoredfit` 関数が `Monitor` オブジェクトを返す場合、`crossvalidation` は表示可能な結合された `Monitor` オブジェクトを返します。これは `BoltzmannMachinesPlots.crossvalidationplot` を介して交差検証プロットを作成することで表示できます。

# オプションの名前付き引数：

  * `kfold`: "`k`-fold" の `k` を指定します（デフォルトは 10）。

    crossvalidation(x, monitoredfit, pars; ...)

さらにパラメータのベクトル `pars` が与えられた場合、`monitoredfit` はパラメータセットからの追加のパラメータも期待します。
