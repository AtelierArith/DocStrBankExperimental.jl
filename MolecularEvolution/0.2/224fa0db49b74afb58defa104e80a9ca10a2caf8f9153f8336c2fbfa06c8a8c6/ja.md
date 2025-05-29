```
lazyprep!(tree::FelNode, initial_message::Vector{<:Partition}; partition_list = 1:length(tree.message), direction::LazyDirection = LazyUp())
```

ツリー全体でメッセージを初期化し、`LazyPartition`を使用してメッセージ伝達アルゴリズムを呼び出す間のツリー準備の追加の中間ステップ。

1. ツリーに対して`lazysort!`を実行し、遅延`felsenstein!`伝播または`sample_down!`のための最適なツリーを取得します。
2. `tree.parent_message`を初期メッセージに固定します。
3. `felsenstein!`伝播または`sample_down!`に必要な十分な数の内部パーティションを事前に割り当てます。
4. 操作の方向（`forward!`、`backward!`）に基づいた特化した準備。`LazyDown`または`LazyUp`。

`LazyDown`、`LazyUp`も参照してください。
