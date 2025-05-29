Struct for Merton Process

```
	mertonProcess=MertonProcess(σ::num1,λ::num2,μ_jump::num3,σ_jump::num4) where {num1,num2,num3,num4<: Number}
```

Where:

```
	σ  =	volatility of the process.
	λ  = 	jumps intensity.
	μ_jump =	jumps mean.
	σ_jump =	jumps variance.
```
