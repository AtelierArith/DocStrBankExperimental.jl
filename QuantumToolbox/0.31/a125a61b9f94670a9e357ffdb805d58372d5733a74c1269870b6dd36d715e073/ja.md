```
bell_state(x::Union{Int}, z::Union{Int})
```

引数 `(x, z)` に応じて [ベル状態](https://en.wikipedia.org/wiki/Bell_state) を返します：

  * `(0, 0)`: $| \Phi^+ \rangle = ( |00\rangle + |11\rangle ) / \sqrt{2}$
  * `(0, 1)`: $| \Phi^- \rangle = ( |00\rangle - |11\rangle ) / \sqrt{2}$
  * `(1, 0)`: $| \Psi^+ \rangle = ( |01\rangle + |10\rangle ) / \sqrt{2}$
  * `(1, 1)`: $| \Psi^- \rangle = ( |01\rangle - |10\rangle ) / \sqrt{2}$

ここで、`x = 1` (`z = 1`) は $| \Phi^+ \rangle$ に対してパウリ-$X$（パウリ-$Z$）ユニタリ変換を適用することを意味します。

# 例

```jldoctest
julia> bell_state(0, 0)

Quantum Object:   type=Ket()   dims=[2, 2]   size=(4,)
4-element Vector{ComplexF64}:
 0.7071067811865475 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
 0.7071067811865475 + 0.0im

julia> bell_state(Val(1), Val(0))

Quantum Object:   type=Ket()   dims=[2, 2]   size=(4,)
4-element Vector{ComplexF64}:
                0.0 + 0.0im
 0.7071067811865475 + 0.0im
 0.7071067811865475 + 0.0im
                0.0 + 0.0im
```

!!! warning "型の安定性に注意！"
    型の安定性を保ちたい場合は、`bell_state(Val(x), Val(z))` を使用することをお勧めします。`bell_state(x, z)` の代わりに。詳細については [このリンク](https://docs.julialang.org/en/v1/manual/performance-tips/#man-performance-value-type) と [関連セクション](@ref doc:Type-Stability) を参照してください。

