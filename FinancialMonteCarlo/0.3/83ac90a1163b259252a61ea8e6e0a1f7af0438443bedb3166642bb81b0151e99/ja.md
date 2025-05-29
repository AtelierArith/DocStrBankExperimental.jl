一般的なインターフェースによるモンテカルロパスからのペイオフ計算

```
	Payoff=payoff(S,optionData,rfCurve,T1=optionData.T)
```

ここで：

```
	S           = 基礎資産のパス。
	optionData  = オプションのデータ。
	rfCurve     = リスクフリー曲線のデータ。
	T1          = スポットシミュレーションの最終時間（デフォルトはオプションの満期までの時間に等しい）[オプション、デフォルトはoptionData.T]

	Payoff      = オプションのペイオフ。
```
