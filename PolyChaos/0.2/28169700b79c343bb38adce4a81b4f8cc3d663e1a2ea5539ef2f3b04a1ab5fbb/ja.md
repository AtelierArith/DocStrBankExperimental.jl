```
computeSP2(n::Integer,β::AbstractVector{<:Real})
computeSP2(n::Integer,op::AbstractOrthoPoly) = computeSP2(n,op.β)
computeSP2(op::AbstractOrthoPoly) = computeSP2(op.deg,op.β)
```

`n` *正則* スカラー積、すなわち直交多項式の 2-ノルムを計算します。すなわち、

$$
\|ϕ_i\|^2 = \langle \phi_i,\phi_i\rangle \quad \forall i \in \{ 0,\dots,n \}.
$$

再帰係数 `(α,β)` の `β` の値のみが必要であることに注意してください。この計算は、Gautschi, W. "Orthogonal Polynomials: Computation and Approximation" の式 (1.3.7) に基づいています。`β` の解析的表現が存在する場合は、この関数を使用するべきです。

この関数は、`AbstractOrthoPoly` との使用を容易にするために、複数のディスパッチに対応しています。
