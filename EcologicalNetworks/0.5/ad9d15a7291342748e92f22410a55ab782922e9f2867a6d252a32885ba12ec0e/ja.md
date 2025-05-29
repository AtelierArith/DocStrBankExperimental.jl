```
n_random_modules(n::Int64)
```

これは*関数*を返し、ネットワークに適用されると、すべての種を `n` モジュールのいずれかにランダムに割り当てます。この関数をネットワーク `N` に適用する正しい方法は、したがって `n_random_modules(4)(N)` です（4つのモジュールで）。

#### 参考文献

Thébault, E., 2013. Identifying compartments in presence–absence matrices and bipartite networks: insights into modularity measures. Journal of Biogeography 40, 759–768. https://doi.org/10.1111/jbi.12015
