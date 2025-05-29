```
Oscillator{T<:Float64}
```

SDOF振動子を表すカスタム型。この型には2つのフィールドがあります：

  * `f_n` は振動子の自然周波数です
  * `ζ_n` は減衰比です

# 例

```julia-repl
    sdof = Oscillator( 1.0, 0.05 )
```
