```
Sine()
```

カスタム一変量分布です。pdfは0とπの間で定義されたサイン関数です。これは、天体測定に軌道をフィッティングする際に使用される一般的な事前分布です。

この分布に対する完全なDistributions.jlインターフェースはまだ定義されていませんが、以下のメソッドは機能します：pdf、logpdf、minimum、maximum、insupport、mean、var、cdf、quantile
