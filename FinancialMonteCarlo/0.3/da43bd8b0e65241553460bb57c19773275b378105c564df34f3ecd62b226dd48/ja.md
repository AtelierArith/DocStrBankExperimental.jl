NIGプロセスの構造体

```
	nigProcess=NormalInverseGaussianProcess(σ::num1,θ::num2,κ::num3) where {num1,num2,num3<: Number}
```

ここで：

```
	σ =	プロセスのボラティリティ。
	θ = ボラティリティの分散。
	κ = ボラティリティの歪度。
```
