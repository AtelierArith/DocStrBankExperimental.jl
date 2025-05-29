```
arma_ssa(d::AbstractIdData, na, nc; L=nothing, estimator=\, robust=false)
```

シンギュラー・スペクトル・分析（SSA）を使用してarmaモデルをフィットします。データに対して低ランク因子分解（svdまたはロバストsvd）が実行され、信号とノイズが分解されます。ノイズはarmaモデルをフィットするための入力として使用されます。

詳細は[`arma`](@ref)を参照してください。

# 引数:

  * `d`:  iddata
  * `na`: 分母パラメータの数
  * `nc`: 分子パラメータの数
  * `L`: 信号とノイズを分離するために使用されるラグ埋め込みの長さ。`nothing`は自動選択に対応します。
  * `estimator`: 最小二乗問題を解決するための関数。例 `\,tls,irls,rtls`。
  * `robust`: 外れ値に対して耐性を持つロバストPCAを使用します。
