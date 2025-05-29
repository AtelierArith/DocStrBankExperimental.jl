Struct for Kou Process

```
	kouProcess=KouProcess(σ::num1,λ::num2,p::num3,λ₊::num4,λ₋::num5) where {num1,num2,num3,num4,num5 <: Number}
```

Where:

```
	σ  =	volatility of the process.
	λ  = 	jumps intensity.
	p  =	prob. of having positive jump.
	λ₊ =	positive jump size.
	λ₋ =	negative jump size.
```
