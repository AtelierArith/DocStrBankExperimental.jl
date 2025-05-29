```julia
struct Hold <: Symbolics.Operator
```

ホールド演算子を表します。連続時間信号は、ゼロ次ホールドで離散時間信号 `x` を保持することによって生成されます。

```
cont_x = Hold()(disc_x)
```
