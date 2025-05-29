```
ExplorationPolicy <: Policy
```

探索ポリシーのための抽象型です。探索ポリシーからのサンプリングは、`action(exploration_policy, on_policy, k, state)`を使用して行われます。`k`は探索パラメータを決定するために使用される値です。通常、これはTD学習アルゴリズムにおけるトレーニングステップです。
