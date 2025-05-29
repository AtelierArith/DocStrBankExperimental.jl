```
Robin{F,P} <: AbstractBoundaryCondition{F,P}
```

フィールド `f` と `p` を持つロビン境界条件（デフォルトは `p = nothing`）。`f` は `f(u, t, p)` の形を持つ関数で、`Tuple` `(a₂, b₂)` を返し、`p` は `f` のパラメータです。

ロビン境界条件は次の形を取ります。

$$
dL/dt = a₂(u, t, p) + b₂(u, t, p)∂u/∂x,
$$

ここで `f(u, t, p) = (a₂(u, t, p), b₂(u, t, p))` です。

# コンストラクタ

```
Robin(f::Function, p = nothing) -> Robin(f, p)
Robin(; f, p = nothing)         -> Robin(f, p)
Robin(a::Number, b::Number)     -> Robin((u, t, p) -> (oftype(u, a), oftype(u, b)))
Robin(a₂::Function, b₂::Function, p = nothing) -> Robin((u, t, p) -> (a₂(u, t, p), b₂(u, t, p)), p)
```
