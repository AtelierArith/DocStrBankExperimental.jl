ブラック・ショールズ・デルタ（欧州オプション用）

```
	Δ=blsdelta(S0,K,r,T,σ,d=0.0,FlagIsCall=true)
```

ここで：

```
	S0         = 基礎資産の価値。
	K          = オプションの行使価格。
	r          = ゼロ金利。
	T          = オプションの満期までの時間。
	σ          = インプライド・ボラティリティ。
	d          = 基礎資産のインプライド・配当。
	FlagIsCall = コールオプションの場合はtrue、プットオプションの場合はfalse。

	Δ          = 欧州オプションのデルタ。
```

# 例

```julia-repl
julia> blsdelta(10.0,10.0,0.01,2.0,0.2,0.01)
0.5452173371920436
```
