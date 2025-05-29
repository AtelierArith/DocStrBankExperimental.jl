このメソッドは残差許容値とネルダー・ミード法、別名単体法を使用します：

```
find_peak(f::Function,
          ms::NelderMeadMethod{FT},
          tol::ResidualTolerance{FT};
          stepping::Bool = false
) where {FT<:AbstractFloat}
```

次の条件で解を見つけます：

  * `f` 解くべき関数
  * `ms` [`NelderMeadMethod`](@ref) 型メソッド構造体
  * `tol` [`ResidualTolerance`](@ref) 型許容構造体
  * `stepping` オプション。trueの場合、最適化ステップをメソッド構造体の履歴フィールドに保存します。
