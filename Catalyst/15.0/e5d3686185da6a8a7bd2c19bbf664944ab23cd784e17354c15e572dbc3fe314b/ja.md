```
save_reactionsystem(filename::String, rn::ReactionSystem; annotate = true, safety_check = true)
```

`ReactionSystem` モデルをファイルに保存します。`ReactionSystem` は実行可能な Julia コードとして保存されます。これは `ReactionSystem` モデルを保存するためにも、簡単に検査するためにファイルに書き込むためにも使用できます。

引数:

  * `filename`: `ReactionSystem` が保存されるファイルの名前。
  * `rn`: ファイルに保存される `ReactionSystem`。
  * `annotate = true`: ファイルに注釈を追加するかどうか。
  * `safety_check = true`: シリアル化後、Catalyst は自動的にシリアル化された `ReactionSystem` をロードし、それが `rn` と等しいかどうかを確認します。等しくない場合、エラーが発生します。`connection_type` フィールドを持たないモデルでは、これは発生しないはずです。パフォーマンスが必要な場合（つまり、大量のモデルを保存する場合）、`safety_check = false` に設定することでこれを無効にできます。

例:

```julia
rn = @reaction_network begin
    (p,d), 0 <--> X
end
save_reactionsystem("rn.jls", rn)
```

モデルは次のようにロードできます。

```julia
rn = include("rn.jls")
```

注意:

  * `connection_type` フィールドを持つ `ReactionSystem` はこれが無視されます（このフィールドの保存はまだ実装されていません）。
  * 非 `ReactionSystem` サブシステム（例: `ODESystem`）を持つ `ReactionSystem` は保存できません。
  * ユニットを持つコンポーネントを持つ反応系は現在保存できません。
  * `ReactionSystem` はモデル作成のために *プログラム的*（DSL ではない）形式で保存されます。

```
