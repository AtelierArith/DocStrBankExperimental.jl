```
RandomMapping(permutations, expansion_size)
RandomMapping(permutations; expansion_size=40)
RandomMapping(;permutations=8, expansion_size=40)
```

入力データを貯水池内で直接ランダムにマッピングします。`expansion_size`は単一の貯水池の次元を決定し、`permutations`は接続される総貯水池の数を決定します。それぞれ異なるマッピングを持っています。この実装の詳細は[1]にあります。

[1] Nichele, Stefano, and Andreas Molund. “Deep reservoir computing using cellular automata.” arXiv preprint arXiv:1703.02806 (2017).
