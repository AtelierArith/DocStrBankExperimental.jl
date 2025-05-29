```
set_output_bounds!(mpc;ymin,ymax,
                ks, soft, binary,prio)
```

時間ステップ k ∈ ks に対して lb ≤ C x  ≤ ub の制約を追加します。

  * `soft` は制約を緩和すべきかどうかを示します（デフォルトは false）
  * `binary` は上限または下限のいずれかを等式で強制すべきかどうかを示します（デフォルトは false）
  * `prio` は制約の相対的な優先度を示します（デフォルトは 0）
