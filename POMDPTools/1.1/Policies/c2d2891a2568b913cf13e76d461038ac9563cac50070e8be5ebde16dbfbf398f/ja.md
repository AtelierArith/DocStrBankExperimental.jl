```
loginfo(::ExplorationPolicy, k)
```

は、探索ポリシーに関する情報を返します。例えば、e-greedyの場合のepsilonやsoftmaxの場合の温度などです。名前付きタプル（例：(temperature=0.5)）を返すことが期待されています。`k`は、探索パラメータを計算するために使用される現在のトレーニングステップです。
