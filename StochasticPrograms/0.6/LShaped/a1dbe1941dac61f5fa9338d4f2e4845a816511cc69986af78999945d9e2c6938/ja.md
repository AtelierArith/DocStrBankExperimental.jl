```
SelectDecaying(T₀::Integer, T̲::Integer = 1, γ::T)
```

[`SelectUniform`](@ref)のように動作しますが、均一な集約サイズは各イテレーションで`γ`だけ減少し、`T₀`から始まります。`T̲`は集約サイズのオプションの下限です。
