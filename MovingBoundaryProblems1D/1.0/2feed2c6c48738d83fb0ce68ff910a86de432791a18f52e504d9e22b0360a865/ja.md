```
Neumann{F,P} <: AbstractBoundaryCondition{F,P}
```

フィールド `f` と `p` を持つ Neumann 境界条件（デフォルトは `p = nothing`）。`f` は `f(u, t, p)` の形の関数であり、`p` は `f` のパラメータです。

Neumann 境界条件は次の形を取ります。

$$
\dfrac{\partial u}{\partial x}(a, t) = f(u(a, t), t, p),
$$

ここで `a` は端点の一つです。

# コンストラクタ

```
Neumann(f::Function, p = nothing) -> Neumann(f, p)
Neumann(; f, p = nothing)         -> Neumann(f, p)
Neumann(v::Number)                -> Neumann((u, t, p) -> oftype(u, v), nothing)
```
