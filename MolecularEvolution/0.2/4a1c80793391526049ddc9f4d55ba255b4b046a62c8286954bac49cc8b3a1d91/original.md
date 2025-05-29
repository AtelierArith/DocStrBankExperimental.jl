```
sim_tree(add_limit::Int,Ne_func,sample_rate_func; nstart = 1, time = 0.0, mutation_rate = 1.0, T = Float64)
```

Simulates a tree of type FelNode{T}. Allows an effective population size function (Ne*func), as well as a sample rate function (sample*rate_func), which can also just be constants.

Ne*func(t) = (sin(t/10)+1)*100.0 + 10.0 root = sim*tree(600,Ne*func,1.0) simple*tree_draw(ladderize(root))
