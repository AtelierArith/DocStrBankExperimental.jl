```
isdigraphical(indegree_sequence, outdegree_sequence)
```

与えられた入次数列と出次数列が有向グラフ的であるかどうか、すなわちそれらが単純な有向グラフ（ループのない有向グラフ）の入次数と出次数の列であることができるかどうかを確認します。これは、`indegree_sequence` と `outdegree_sequence` が独立ではなく、それぞれの要素が頂点が持つべき入次数と出次数を表すことを意味します。

### 実装ノート

Fulkerson-Chen-Anstee定理によれば、列 $\{(a_1, b_1), ...,(a_n, b_n)\}$（aの降順にソートされたもの）がグラフィックであるための条件は、$\sum_{i = 1}^{n} a_i = \sum_{i = 1}^{n} b_i$ であり、かつその列が以下の性質に従うことです -

$$
\sum_{i=1}^{r} a_i \leq \sum_{i=1}^n min(r-1,b_i) + \sum_{i=r+1}^n min(r,b_i)
$$

各整数 1 <= r <= n-1 に対して。

参照: [`isgraphical`](@ref)
