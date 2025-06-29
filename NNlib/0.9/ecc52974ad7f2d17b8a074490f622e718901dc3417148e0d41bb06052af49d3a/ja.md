```
rrelu(x, lo=1/8, hi=1/3) = max(a*x, x)
# ここで `a` は一様分布 `U(lo, hi)` からランダムにサンプリングされます
```

ランダム化されたリーキー整流線形ユニット活性化関数。詳細は ["Empirical Evaluation of Rectified Activations"](https://arxiv.org/abs/1505.00853) を参照してください。境界を明示的に指定することもできます。例えば、`rrelu(x, 0.0, 1.0)` のように。

```julia-repl
julia> lineplot(rrelu, -20, 10, height=7)
            ┌────────────────────────────────────────┐         
         10 │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⠀⠀⠀⠀⠀⠀⠀⠀⠀⣀⡤⠖⠋│ rrelu(x)
            │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⠀⠀⠀⠀⠀⢀⡠⠖⠋⠁⠀⠀⠀│         
            │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⠀⢀⡠⠔⠊⠁⠀⠀⠀⠀⠀⠀⠀│         
   f(x)     │⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⢤⡤⠤⣤⣤⢤⣤⣤⠤⠤⠤⢼⠮⠥⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤│         
            │⣰⢀⣆⡄⣄⡄⡠⡰⠦⠷⡜⢢⠷⠳⠢⠊⠉⠉⠀⠀⠁⠀⠀⠀⠀⠀⢸⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│         
            │⠃⠉⠙⠘⠃⠈⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│         
        -10 │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│         
            └────────────────────────────────────────┘         
            ⠀-20⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀10⠀         
            ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀x⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀         

julia> extrema(rrelu.(fill(-10f0, 1000)))
(-3.3316886f0, -1.2548422f0)
```
