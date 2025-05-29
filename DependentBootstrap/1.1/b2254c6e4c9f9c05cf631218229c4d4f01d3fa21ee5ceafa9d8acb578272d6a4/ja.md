```
dboot(data, bi::BootInput)
dboot(data ; kwargs...)
```

データセットに関連するレベル2のブートストラップ統計を取得し、BootInputのブートストラップ手法を使用します。

BootInputのキーワードコンストラクタを呼び出すキーワードメソッドも提供されています。詳細なキーワードについては、REPLで?BootInputを使用してください。

出力の戻り値の型はbi.flevel2によって決定されます。bi.flevel2は、Tがbi.flevel1の出力型であるVector{T}を受け入れる関数でなければなりません。

例えば、dataがVector{<:Number}であり、bi.flevel1がmeanである場合、この場合、bi.flevel1はFloat64を返し、したがってbi.flevel2はVector{Float64}を入力として受け入れる関数でなければなりません（出力型は任意で構いません）。

あるいは、bi.flevel2は匿名関数(x -> quantile(x, [0.025, 0.975]))であり、この場合、入力はVector{Float64}であり、したがってbi.flevel1はFloat64を返す必要があります。この場合、bi.flevel2の出力は、入力データセットのレベル1統計に対するブートストラップ95%信頼区間に対応する要素を持つ2要素のVector{Float64}になります。
