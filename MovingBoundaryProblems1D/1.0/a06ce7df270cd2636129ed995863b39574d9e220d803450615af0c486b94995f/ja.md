```
Dirichlet{F,P} <: AbstractBoundaryCondition{F,P}
```

フィールド `f` と `p` を持つディリクレ境界条件（デフォルト `p = nothing`）。ここで `f` は `f(u, p)` の形の関数であり、`p` は `f` のパラメータです。

ディリクレ境界条件は次の形を取ります。

$$
u(a, t) ↤ f(u(a, t), t, p),
$$

ここで `a` は端点の一つです。

# コンストラクタ

```
Dirichlet(f::Function, p = nothing) -> Dirichlet(f, p)
Dirichlet(; f, p = nothing)         -> Dirichlet(f, p)
Dirichlet(v::Number)                -> Dirichlet((u, t, p) -> oftype(u, v), nothing)
```
