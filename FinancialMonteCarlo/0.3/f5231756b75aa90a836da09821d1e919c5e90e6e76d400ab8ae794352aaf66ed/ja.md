Mertonプロセスの構造体

```
	mertonProcess=MertonProcess(σ::num1,λ::num2,μ_jump::num3,σ_jump::num4) where {num1,num2,num3,num4<: Number}
```

ここで：

```
	σ  =	プロセスのボラティリティ。
	λ  = 	ジャンプの強度。
	μ_jump =	ジャンプの平均。
	σ_jump =	ジャンプの分散。
```
