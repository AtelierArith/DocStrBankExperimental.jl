```
thermal_dm(N::Int, n::Real; sparse::Union{Bool,Val}=Val(false))
```

熱状態の密度行列（熱状態の確率を生成）で、以下の引数を持ちます：

  * `N::Int`: ヒルベルト空間の基底状態の数
  * `n::Real`: 熱状態における粒子数の期待値。
  * `sparse::Union{Bool,Val}`: `true`の場合、スパース行列表現を返します。

!!! warning "型の安定性に注意してください！"
    型の安定性を保ちたい場合は、`thermal_dm(N, n, sparse=Val(sparse))`を使用することをお勧めします。`thermal_dm(N, n, sparse=sparse)`の代わりに。詳細については、[このリンク](https://docs.julialang.org/en/v1/manual/performance-tips/#man-performance-value-type)と、型の安定性に関する[関連セクション](@ref doc:Type-Stability)を参照してください。

