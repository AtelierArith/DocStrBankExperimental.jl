```
one_sided_stretch((x0, x1), N::Int, α)
```

片側のtanhストレッチング関数を適用します。`(x0, x1)`ポイントは希望する端点を表し、`N`はポイントの数、`α`はストレッチングファクターです（推奨値は約10を超えないこと）。デフォルトオプションは`x0`の近くにクラスタリングしますが、`cluster_on_x0=false`を設定すると`x1`の近くにクラスタリングします。
