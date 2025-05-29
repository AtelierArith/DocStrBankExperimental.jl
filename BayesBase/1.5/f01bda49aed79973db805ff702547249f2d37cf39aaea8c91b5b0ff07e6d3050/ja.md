```
ContinuousMultivariateLogPdf{ D <: DomainSets.Domain, F } <: AbstractContinuousGenericLogPdf
```

ドメイン仕様とログpdf関数の形での一般的な連続多変量分布。既知の解析分布が利用できない場合に使用できます。

# 引数

  * `domain`: `DomainSets.jl`パッケージからの多次元ドメイン仕様。ドメインチェックを回避するには`BayesBase.UnspecifiedDomain()`を使用します。
  * `logpdf`: `AbstractVector`を入力として受け取り、ログ密度を表す呼び出し可能なオブジェクト。正規化されていない場合があります。
