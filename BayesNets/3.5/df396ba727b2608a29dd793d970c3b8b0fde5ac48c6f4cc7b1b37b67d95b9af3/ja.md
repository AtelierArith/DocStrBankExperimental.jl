```
rand_discrete_bn(num_nodes16, max_num_parents=3,
        max_num_states=5, connected=true)
```

ランダムな DiscreteBayesNet を生成します。

`num_nodes` ノードを持つ DiscreteBayesNet を作成し、各ノードはそれぞれ `max_num_parents` および `max_num_states` までのランダムな数の状態と親を持ちます。`connected` が true の場合、各ノード（最初のノードを除く）は少なくとも1つの親を持つことが保証され、グラフは接続されます。
