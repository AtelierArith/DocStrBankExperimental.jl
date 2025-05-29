```
rrelu(x, lo=1/8, hi=1/3) = max(a*x, x)
# where `a` is randomly sampled from uniform distribution `U(lo, hi)`
```

Randomized Leaky Rectified Linear Unit activation function. See ["Empirical Evaluation of Rectified Activations"](https://arxiv.org/abs/1505.00853) You can also specify the bound explicitly, e.g. `rrelu(x, 0.0, 1.0)`.

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
