一般的なデルタインターフェース

```
	Delta=delta(mcProcess,rfCurve,mcConfig,abstractPayoff,dS0)
```

ここで：

```
	mcProcess      = シミュレーションされるプロセス。
	rfCurve        = ゼロ金利データ。
	mcConfig       = モンテカルロシミュレーションの基本的なプロパティ
	abstractPayoff = 価格設定されるペイオフ
	dS0            = 増分 [オプション、デフォルトは1e-7]
	
	Delta          = デリバティブのデルタ
```
