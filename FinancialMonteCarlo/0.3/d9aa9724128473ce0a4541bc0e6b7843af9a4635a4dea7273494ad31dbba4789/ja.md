一般的なRho計算のインターフェース

```
	Rho=rho(mcProcess,rfCurve,mcConfig,abstractPayoff,dr)
```

ここで：

```
	mcProcess      = シミュレーションされるプロセス。
	rfCurve        = ゼロレートデータ。
	mcConfig       = モンテカルロシミュレーションの基本的なプロパティ
	abstractPayoff = 価格設定されるペイオフ(s)
	dr             = 増分 [オプション、デフォルトは1e-7]

	Rho            = デリバティブのRho
```
