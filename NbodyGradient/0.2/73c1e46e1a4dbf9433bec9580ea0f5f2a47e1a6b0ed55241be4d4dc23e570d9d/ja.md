```
Integrator{T<:AbstractFloat}
```

Integrator。[`State`](@ref)を統合するためのファンクタとして使用されます。

# フィールド

  * `scheme::Function` : 使用する統合スキーム。
  * `h::T` : ステップサイズ。
  * `t0::T` : 初期時間。
  * `tmax::T` : シミュレーションの期間。
