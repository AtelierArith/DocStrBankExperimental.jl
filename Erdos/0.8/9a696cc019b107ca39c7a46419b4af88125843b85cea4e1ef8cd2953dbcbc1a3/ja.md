```
static_fitness_model(m, fitness, G=Graph; seed=-1)
static_fitness_model(m, fitness_out, fitness_in, G=DiGraph; seed=-1)
```

`length(fitness)` ノードと `m` エッジを持つランダムグラフを生成します。このグラフでは、エッジ `(i, j)` の存在確率は `fitness[i]*fitness[j]` に比例します。時間計算量は O(|V| + |E| log |E|) です。

有向グラフを生成するためには、入出力フィットネスを提供する必要があります。

参考文献:

  * Goh K-I, Kahng B, Kim D: Universal behaviour of load distribution

in scale-free networks. Phys Rev Lett 87(27):278701, 2001.
