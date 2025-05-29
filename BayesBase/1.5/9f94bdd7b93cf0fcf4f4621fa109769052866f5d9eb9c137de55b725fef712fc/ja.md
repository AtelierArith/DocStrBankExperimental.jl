```
ContinuousUnivariateLogPdf{ D <: DomainSets.Domain, F } <: AbstractContinuousGenericLogPdf
```

ドメイン仕様とlogpdf関数の形を持つ一般的な連続一変量分布。既知の解析分布が利用できない場合に使用できます。

# 引数

  * `domain`: `DomainSets.jl`パッケージからのドメイン仕様、デフォルトでは`domain`は`DomainSets.FullSpace()`に設定されています。ドメインチェックをバイパスするには`BayesBase.UnspecifiedDomain()`を使用してください。
  * `logpdf`: ログ密度を表す呼び出し可能なオブジェクト。正規化されていない場合があります。
