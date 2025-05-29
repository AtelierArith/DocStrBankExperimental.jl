```
gpslc(filename * ".csv")
gpslc(filename * ".csv"; hyperparams=hyperparams, priorparams=priorparams))

gpslc(DataFrame(X1=...,X2=...,T=...,Y=...,obj=...))
gpslc(DataFrame(X1=...,X2=...,T=...,Y=...,obj=...); hyperparams=hyperparams, priorparams=priorparams)
```

入力データに対して事後推論を実行します。

DataFrameまたはCSVのデータ型は以下の基準に従う必要があります：

  * `T` (Boolean/Float64)
  * `Y` (Float64)
  * `X1...XN` (Float64...Float64)
  * `obj` (Any)

オプションのパラメータ

  * `hyperparams::`[`HyperParameters`](@ref)=[`getHyperParameters`](@ref)`()`: ハイパーパラメータは、主に実行する推論の高レベルの量を定義します。
  * `priorparams::`[`PriorParameters`](@ref)=[`getPriorParameters`](@ref)`()`: プライヤーパラメータは、カーネル関数と潜在的な交絡因子構造を構築する際に引き出す高レベルの事前分布を定義します。

[`GPSLCObject`](@ref)を返し、ハイパーパラメータ、事前パラメータ、データ、および事後サンプルを格納します。
