```
QuickPOMDP(gen::Function, [id]; kwargs...)
```

関数 `gen` とキーワード引数を使って生成的POMDPモデルを構築します。

`gen` は3つの引数を取る必要があります：状態、アクション、そして乱数生成器。次の状態のためのキー `sp`、観測のためのキー `o`、報酬のためのキー `r` を持つ `NamedTuple` を返す必要があります。

キーワードは静的オブジェクトまたは関数であることができます。詳細については、QuickPOMDPs.jlのドキュメントを参照してください。 ```
