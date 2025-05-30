Kouプロセスの構造体

```
	kouProcess=KouProcess(σ::num1,λ::num2,p::num3,λ₊::num4,λ₋::num5) where {num1,num2,num3,num4,num5 <: Number}
```

ここで：

```
	σ  =	プロセスのボラティリティ。
	λ  = 	ジャンプの強度。
	p  =	正のジャンプが発生する確率。
	λ₊ =	正のジャンプサイズ。
	λ₋ =	負のジャンプサイズ。
```
