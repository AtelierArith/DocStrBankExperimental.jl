```
GraphShortestPathEnv([rng]; n=10, sparsity=0.1, max_steps=10)
```

引用された**A.3**は、論文[Decision Transformer: Reinforcement Learning via Sequence Modeling](https://arxiv.org/abs/2106.01345)にあります。

> 我々は、序論で議論された例の詳細を示します。このタスクは、固定された有向グラフ上で最短経路を見つけることであり、報酬が0であるのはエージェントがゴールノードにいるときであり、それ以外の場合は−1です。この観察は、エージェントがいるグラフノードの整数インデックスです。アクションは、次に移動するグラフノードの整数インデックスです。遷移ダイナミクスは、グラフにエッジがある場合、エージェントをアクションのノードインデックスに移動させ、そうでない場合は過去のノードに留まります。この問題における将来のリターンは負の経路長に対応し、それを最大化することは最短経路を生成することに対応します。

