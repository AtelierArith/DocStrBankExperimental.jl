```
LogUpdate(ζ = 0.08) <: ShiftStrategy
```

シフトをログ式に従って更新するための戦略で、減衰パラメータ `ζ` を使用します。

$$
S^{n+1} = S^n -\frac{ζ}{dτ}\ln\left(\frac{\|Ψ\|_1^{n+1}}{\|Ψ\|_1^n}\right)
$$

[`ShiftStrategy`](@ref) および [`ProjectorMonteCarloProblem`](@ref) を参照してください。
