```
order_from_tree_decomposition(td::Dict{Symbol, Any}; root::Symbol=:b_1)
```

与えられた木分解と同じ木幅を持つ頂点消去順序を返します。

頂点消去順序を構築するために使用されるアルゴリズムは、以下の論文でShutskiらによって説明されています https://doi.org/10.1103/PhysRevA.102.062614

# キーワード

  * `root::Symbol=:b_1`: 根として取る木のノード。`n`が1から木分解の袋の数までの整数である形のシンボル`:b_n`でなければなりません。
