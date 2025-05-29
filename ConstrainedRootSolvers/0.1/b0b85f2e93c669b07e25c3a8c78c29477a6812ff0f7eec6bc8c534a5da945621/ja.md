このメソッドは[`ReduceStepMethod`](@ref)メソッドを使用します：

```
find_zero(f::Function,
          ms::ReduceStepMethod{FT},
          tol::Union{ResidualTolerance{FT}, SolutionTolerance{FT}};
          stepping::Bool = false
) where {FT<:AbstractFloat}
```

ターゲット関数がゼロである解を返します。与えられるもの：

  * `f` 解く関数
  * `ms` [`ReduceStepMethod`](@ref)型メソッド構造体
  * `tol` [`ResidualTolerance`](@ref)または[`SolutionTolerance`](@ref)型の許容誤差構造体
  * `stepping` オプション。trueの場合、最適化ステップをメソッド構造体の履歴フィールドに保存します。
