```
sim_tree(add_limit::Int,Ne_func,sample_rate_func; nstart = 1, time = 0.0, mutation_rate = 1.0, T = Float64)
```

FelNode{T}型の木をシミュレートします。効果的な個体群サイズ関数（Ne*func）や、定数としても使用できるサンプルレート関数（sample*rate_func）を許可します。

Ne*func(t) = (sin(t/10)+1)*100.0 + 10.0 root = sim*tree(600,Ne*func,1.0) simple*tree_draw(ladderize(root))
