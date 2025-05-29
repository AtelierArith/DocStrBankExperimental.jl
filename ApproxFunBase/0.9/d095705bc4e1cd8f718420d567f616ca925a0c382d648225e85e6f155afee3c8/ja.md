```
evaluate(coefficients::AbstractVector, sp::Space, x)
```

`domain(sp)`にある点`x`で展開を評価します。`x`がドメインにない場合、返される値は空間に依存し、信頼できるものではありません。ドメイン外の値で関数を評価するには、[`extrapolate`](@ref)を参照してください。
