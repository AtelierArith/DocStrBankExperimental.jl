```
Reddit(; full=true, dir=nothing)
```

RedditデータセットはRef [1]で紹介されました。これは2014年9月に投稿されたRedditの投稿のグラフデータセットです。このデータセットには、同じユーザーが両方にコメントした場合に投稿を接続する単一の投稿間グラフが含まれています。この場合、ノードラベルは投稿が属する41のコミュニティ、または「サブレディット」のいずれかです。このデータセットには232,965件の投稿が含まれています。最初の20日間はトレーニングに使用され、残りの日はテストに使用されます（30%は検証に使用）。各ノードは602の単語ベクトルで表されます。

`full=false`を使用して、データセットのサブサンプルのみをロードします。

# 参考文献

[1]: [Inductive Representation Learning on Large Graphs](https://arxiv.org/abs/1706.02216)

[2]: [Benchmarks on the Reddit Dataset](https://paperswithcode.com/dataset/reddit)
