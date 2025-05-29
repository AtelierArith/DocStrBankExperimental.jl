```
SPABoot(data ; alpha, kernelfunction, bandwidth, bootinput_kwargs...)
```

依存ブートストラップを使用してSPAテストを行うためのメソッドタイプ。データといくつかのキーワード引数を受け取るコンストラクタが提供されています。データは、ベースケースに対する各予測の損失差を指します。詳細については、?spaを参照してください。関連するキーワード引数は次のとおりです：

```
alpha=0.05 <- テストで使用する信頼水準 

kernelfunction=KernelEpanechnikov() <- HAC分散推定器とともに使用するカーネル関数。詳細については、?hacvarianceを参照してください。 

bandwidth=-1 <- HAC分散推定器のバンド幅。bandwidth <= -1の場合、バンド幅はPolitis (2003)の「適応バンド幅選択」を使用して推定されます。 

blocklength=0.0 <- ブートストラップで使用するブロック長。0.0のデフォルトは、ブロック長がデータから最適に推定されることを意味し、DependentBootstrapパッケージによって最も適切と見なされる方法（通常はPatton、Politis、およびWhite (2009)の選択手順）を使用します。 

numresample=1000 <- ブートストラップ時に使用するリサンプルの数。 

bootmethod=:stationary <- 使用するブートストラップ方法論で、デフォルトはPolitisとRomano (1993)の定常ブートストラップです。
```

注意：BootInputコンストラクタの有効なキーワード引数に関する詳細は、DependentBootstrapのドキュメントを参照してください。
