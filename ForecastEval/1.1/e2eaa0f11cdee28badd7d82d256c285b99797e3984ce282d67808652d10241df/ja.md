```
DMHAC(data ; alpha::Float64=0.05, kernelfunction, bandwidth::Int=-1)
```

HAC分散推定量を使用したDiebold-Marianoテストを行うためのメソッドタイプ。データと3つのキーワード引数を受け取るコンストラクタが提供されています。関連するキーワード引数は次のとおりです：

```
alpha <- テストの信頼水準

kernelfunction <- HAC分散推定量で使用するカーネル関数。有効な値は
    KernelEpanechnikov(), KernelGaussian(), KernelUniform(), KernelBartlett()です。また、:epanechnikov、:gaussian、:uniform、:bartlett、またはこれらのシンボルの文字列バリアントも使用できます。

bandwidth <- HAC分散推定量で使用するバンド幅（-1以下に設定すると、Politis (2003) の「適応バンド幅選択」を使用してバンド幅を推定します）
```
