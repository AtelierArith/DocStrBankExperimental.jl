```
macro parameters(args...)
```

`SimulationParameters`を作成し、実際の構造体の型はマクロに渡された引数によって決定されます。

# 例

```julia
# T₁およびT₂の値を持つStructArray{T₁T₂}を作成
T₁, T₂ = rand(100), 0.1*rand(100)
parameters = @parameters T₁ T₂

# T₁、T₂およびB₁の値を持つStructArray{T₁T₂B₁}を作成
T₁, T₂, B₁ = rand(100), 0.1*rand(100), ones(100)
parameters = @parameters T₁ T₂ B₁

# T₁、T₂およびB₀の値を持つStructArray{T₁T₂B₀}を作成
# 今回はユニコード文字を使用しないエイリアスを使用
T1, T2, B0 = rand(100), 0.1*rand(100), ones(100)
parameters = @parameters T1 T2 B0
```
