```
add_constraint!(mpc::MPC;
    Ax, Au, Ar, Aw, Ad, Aup,
    ub, lb, ks, soft, binary, prio)
add_constraint!(mpc;Ax,Au,ub,lb,
                ks, soft, binary,prio)
```

制約 lb ≤ Ax xₖ + Au uₖ ≤ ub を時間ステップ k ∈ ks に対して追加します（追加の項 Ar rₖ, Aw wₖ, Ad dₖ, Aup u⁻ₖ が可能です）

  * `soft` は制約を緩和すべきかどうかを示します（デフォルトは false）
  * `binary` は上限または下限のいずれかを等式で強制すべきかどうかを示します（デフォルトは false）
  * `prio` は制約の相対的な優先度を示します（デフォルトは 0）
