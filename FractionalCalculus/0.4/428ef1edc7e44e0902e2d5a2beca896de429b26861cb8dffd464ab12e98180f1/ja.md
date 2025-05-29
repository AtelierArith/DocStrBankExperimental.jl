```
fracint(f, α, point, h, FracIntAlg())
```

分数積分計算に使用される一般的な関数です。

### 例

```julia-repl
julia> fracint(x->x^2, 0.5, 1, 0.001, RLInt_Approx())
0.6017877646029814
```

分数積分を計算するために使用できる多くのアルゴリズムがあります。詳細については、マニュアルを参照してください: [manual](http://scifracx.org/FractionalCalculus.jl/dev/Integral/integralapi/).
