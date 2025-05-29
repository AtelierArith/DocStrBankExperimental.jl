```
StochasticModel(X, p)
```

確率的プログラム `X` をパラメータ `p` と組み合わせて、[Functors](https://fluxml.ai/Functors.jl/stable/) を使用して学習可能なモデルにします。ここで、`p <: AbstractArray` です。最小化問題として定式化します。すなわち、$\mathbb{E}[X(p)]$ を最小化する $p$ を見つけます。
