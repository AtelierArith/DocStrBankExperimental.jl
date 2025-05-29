```
one_sided_with_initial_spacing((x0, x1), N::Int, dx0; cluster_on_x0=true)
```

初層での間隔を指定しつつ、一方向のtanhストレッチング関数を適用します。`(x0, x1)`ポイントは希望する端点を表し、`N`はポイントの数です。デフォルトのオプションは`x0`の近くにクラスタリングすることですが、`cluster_on_x0=false`に設定すると`x1`の近くにクラスタリングされます。
