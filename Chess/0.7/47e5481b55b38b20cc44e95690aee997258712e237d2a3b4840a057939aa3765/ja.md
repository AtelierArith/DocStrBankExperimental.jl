```
forward!(g::SimpleGame)
forward!(g::Game)
forward!(g::Game, m::Move)
forward!(g::Game, m::String)
```

ゲームを進めるために、以前に撤回された手を再生します。

すでにゲームの終わりにいる場合、ゲームは変更されません。現在のノードに複数の子ノードがある場合、常に最初の子ノード（つまりメインライン）を選択します。最初の子ノード以外の子ノードが必要な場合は、第二引数としてその子ノードに至る手を指定してください。提供された手が既存の子ノードのいずれかに至ることを呼び出し元が責任を持つ必要があります。
