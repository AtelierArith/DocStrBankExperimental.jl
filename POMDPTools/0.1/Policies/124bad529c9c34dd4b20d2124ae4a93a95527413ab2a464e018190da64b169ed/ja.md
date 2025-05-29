```
VectorPolicy{S,A}
```

アクションのベクトルからなる一般的なMDPポリシーです。`stateindex(mdp, s)`のエントリは、状態`s`で取られるアクションです。

# フィールド

  * `mdp::MDP{S,A}` MDP問題
  * `act::Vector{A}` 状態インデックスをアクションにマッピングするサイズ|S|のベクトル
