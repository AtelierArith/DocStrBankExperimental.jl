```
forward!(dest::Partition, source::Partition, model::BranchModel, node::FelNode)
```

モデルに基づいて、ソースパーティションをブランチに沿ってデスティネーションパーティションに前方に伝播させます。注意: 自分のBranchModelタイプに対してこれをオーバーロードする必要があります。
