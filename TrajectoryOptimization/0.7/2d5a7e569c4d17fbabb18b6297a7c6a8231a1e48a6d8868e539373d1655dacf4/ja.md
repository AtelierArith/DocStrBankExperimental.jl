```
NormConstraint{S,D,T}
```

形の制約 $\|y\|_2 \leq a$ で、$y$ は状態および/または制御ベクトルの要素で構成されています。これは等式制約、例えば $y^T y - a^2 = 0$、不等式制約、$y^T y - a^2 \leq 0$、または二次制約である可能性があります。

# コンストラクタ:

```
NormConstraint(n, m, a, sense, [inds])
```

ここで `n` は状態の数、`m` は制御の数、`a` は方程式の右辺の定数、`sense` は `Inequality()`, `Equality()`, または `SecondOrderCone()` であり、`inds` は `UnitRange`、`AbstractVector{Int}`、または `:state` または `:control` のいずれかです。

# 例:

```julia
NormConstraint(3, 2, 4, Equality(), :control)
```

は、2つの制御を持つ問題に対して $\|u\|^2 = 16.0$ に相当する制約を作成します。

```julia
NormConstraint(3, 2, 3, Inequality(), :state)
```

は、3つの状態を持つ問題に対して $\|x\|^2 \leq 9$ に相当する制約を作成します。

```julia
NormConstraint(3, 2, 5, SecondOrderCone(), :control)
```

は、$\|x\|_2 \leq 5$ に相当する制約を作成します。
