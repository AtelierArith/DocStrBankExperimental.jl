# アタニャンガ・セダアルゴリズムによるカプート-ファブリツィオ分数微分の近似

```
fracdiff(f, α, point, h, CaputoFabrizioAS())
```

### 例

```julia-repl
julia> fracdiff(x->x, 0.5, 1, 0.001, CaputoFabrizioAS())
0.9893315392351845
```

### 参考文献

```tex
Fractional Stochastic Differential Equations
```
