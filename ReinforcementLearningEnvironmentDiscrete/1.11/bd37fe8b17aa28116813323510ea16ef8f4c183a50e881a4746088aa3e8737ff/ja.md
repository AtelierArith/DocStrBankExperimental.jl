```
treeMDP(na, depth; init = "random", branchingfactor = 3)
```

naのアクションと木の`depth`を持つ木構造のMDPを返します。`init`がランダムの場合、`branchingfactor`は（アクション、状態）ペアが持つ可能な状態の数を決定します。`init = "deterministic"`の場合、`branchingfactor = na`です。
