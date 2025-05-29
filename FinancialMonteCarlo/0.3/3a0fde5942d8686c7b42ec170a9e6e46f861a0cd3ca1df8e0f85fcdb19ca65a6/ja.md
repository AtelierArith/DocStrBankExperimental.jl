価格の信頼区間の計算のための一般インターフェース

```
	IC=confinter(mcProcess,rfCurve,mcConfig,abstractPayoff,alpha)
```

ここで：

```
	mcProcess      = シミュレーションされるプロセス。
	rfCurve        = ゼロレートデータ。
	mcConfig       = モンテカルロシミュレーションの基本的なプロパティ
	abstractPayoff = 価格設定されるペイオフ
	alpha          = 信頼水準 [オプション、デフォルトは99%]

	Price          = デリバティブの価格
```
