```
A_scaled, D1, D2 = equilibrate(A::AbstractMatrix{T}; A_transposed = false, kwargs...)
```

行列 `A` に対して平衡化アルゴリズムを実行し、対角スケーリング係数 `D1` と `D2` を持つスケーリングされた行列 `A_scaled` を返します。

```
Q_scaled, D = equilibrate(Q::Symmetric{T}; kwargs...) where {T}
```

対称行列 `Q` に対して平衡化アルゴリズムを実行し、対角スケーリング係数 `D` を持つスケーリングされた行列 `Q_scaled` を返します。

キーワード引数については [`equilibrate!`](@ref) を参照してください。
