```
`BacktestResult`オブジェクトを作成します。`dataset`は、Value-at-Riskのバックテストが実施されたデータセットの名前を指定します。`vm`は、Value-at-Riskの推定値を取得するために使用される`VaRModel`を指定します。`windowsize`は、各アウトオブサンプルVaR予測を取得するために使用されたインサンプル観測の数を指定します。`level`はVaRの分位数レベルです。`data`は実現のベクトルであり、`vars`はVaR推定値のベクトルです。オプションのパラメータ`lags`は、VaR推定値の違反/ヒットシーケンスの時間的独立性をテストするために`DQTest`および`LjungBoxTest`で使用されるラグの数を指定します。
```
