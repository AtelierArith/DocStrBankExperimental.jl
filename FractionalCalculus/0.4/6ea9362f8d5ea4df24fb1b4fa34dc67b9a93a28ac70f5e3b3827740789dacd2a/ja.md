```
fracdiff(f, α, point, h, FracDiffAlg())
```

`fracdiff` は分数導関数を計算するための一般的な関数です。

### 例

```julia-repl
julia> fracdiff(x->x^2, 0.5, 1, 0.001, RLDiffL1())
1.5044908143658473
```

分数導関数を計算するために使用できる多くのアルゴリズムがあります。詳細については、マニュアルを参照してください: http://scifracx.org/FractionalCalculus.jl/dev/Derivative/derivativeapi/.
