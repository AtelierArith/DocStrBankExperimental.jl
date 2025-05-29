```
max_abs_speed_naive(u_ll, u_rr, orientation::Integer, equations)
max_abs_speed_naive(u_ll, u_rr, normal_direction::AbstractVector, equations)
```

左状態 `u_ll` と右状態 `u_rr` に関連する局所的な波速度のみに基づいて、リーマン問題の最大波速度の単純で迅速な推定を行います。

1次元の非整数引数 `normal_direction` に対して、`max_abs_speed_naive` は `abs(normal_direction[1]) * max_abs_speed_naive(u_ll, u_rr, 1, equations)` を返します。
