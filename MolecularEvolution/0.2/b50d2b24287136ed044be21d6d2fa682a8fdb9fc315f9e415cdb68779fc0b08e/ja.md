```
backward!(dest::Partition, source::Partition, model::BranchModel, node::FelNode)
```

モデルに基づいて、ソースパーティションをブランチに沿ってデスティネーションパーティションに逆伝播します。注意: 自分のBranchModelタイプに対してこれをオーバーロードする必要があります。
