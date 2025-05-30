確率過程シミュレーションの一般インターフェース

```
	S=simulate(mcProcess,zeroCurve,mcBaseData,T)
```

ここで：

```
	mcProcess   = シミュレーションされるプロセス。
	zeroCurve   = ゼロ金利曲線のデータ。
	mcBaseData  = モンテカルロシミュレーションの基本的な特性
	T           = プロセスの最終時刻

	S           = 基礎となるパスの行列。
```
