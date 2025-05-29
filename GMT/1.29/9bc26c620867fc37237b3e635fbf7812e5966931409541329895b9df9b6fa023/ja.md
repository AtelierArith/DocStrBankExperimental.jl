```
qqplot(x::AbstractVector{AbstractFloat}, y::AbstractVector{AbstractFloat}; kwargs...)
```

qqplot関数は、2つの分布の分位数を比較します。

  * `qqline`: Q-Qプロットのフィットラインを計算する方法を決定します。オプションは次の通りです。

      * `identity`: y = xのラインを描画します（デフォルト）。
      * `fit`: 分位数ペアの最小二乗フィットラインを描画します。
      * `fitrobust`または`quantile`: 分布の第1四分位数と第3四分位数を通るラインを描画します。
      * `none`: ラインを描画しません。

    一般的に、`qqline=:identity`はxとyが同じ分布に従うかどうかを確認するのに役立ち、`qqline=:fit`および`qqline=:fitrobust`はyの分布がxの分布からアフィン変換を通じて得られるかどうかを確認するのに役立ちます。
  * ラインと散布点の微調整には、`plot`モジュールと同じオプションを使用します。

例:

```
qqplot(randn(100), randn(100), show=true)

qqplot(randn(100), show=true)
```
