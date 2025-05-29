価格の分散区間の計算のための一般インターフェース

```
	variance_=variance(mcProcess,rfCurve,mcConfig,abstractPayoff)
```

ここで：

```
	mcProcess      = シミュレーションされるプロセス。
	rfCurve        = ゼロレートデータ。
	mcConfig       = モンテカルロシミュレーションの基本的なプロパティ
	abstractPayoff = 価格設定されるペイオフ(s)

	variance_      = デリバティブのペイオフの分散
```
