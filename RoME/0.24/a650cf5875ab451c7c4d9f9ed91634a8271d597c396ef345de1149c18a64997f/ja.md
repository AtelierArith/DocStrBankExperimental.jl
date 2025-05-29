```julia
getLastPoses(dfg; filterLabel, number)

```

`filterLabel::Regex` に従って、最後の `number::Int` のポーズを返します。

ノート

  * 検索インデックスとして、変数の履歴を分散因子グラフオブジェクトにFIFOで追加します。

開発ノート

  * TODO: IIF内の変数ラベルに対する正規表現による一般的なフィルタと統合する。
