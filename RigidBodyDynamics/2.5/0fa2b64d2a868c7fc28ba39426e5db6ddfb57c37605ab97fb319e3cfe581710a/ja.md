```julia
rand_tree_mechanism(_, parentselector, jointtypes)

```

与えられた関節タイプを持つランダムツリー `Mechanism` を作成します。各新しいボディは、`parentselector` 関数を使用して選択された親に接続されます。
