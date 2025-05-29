```
max_abs_speed(u_ll, u_rr, orientation::Integer, equations)
max_abs_speed(u_ll, u_rr, normal_direction::AbstractVector, equations)
```

左状態 `u_ll` と右状態 `u_rr` に関連する局所波速度のみに基づいて、リーマン問題の最大波速度の簡単で迅速な推定です。 [`max_abs_speed_naive`](@ref) よりも拡散が少なく、すなわち過大評価しています。

特に、`max_abs_speed(u, u, i, equations)` は `max_abs_speeds(u, equations)[i]` と同じ結果を返します。これは、[`StepsizeCallback`](@ref) を通じて最大安定時間ステップサイズを計算する `max_dt` で使用される波速度です。

1次元の非整数引数 `normal_direction` に対して、`max_abs_speed_naive` は `abs(normal_direction[1]) * max_abs_speed_naive(u_ll, u_rr, 1, equations)` を返します。
