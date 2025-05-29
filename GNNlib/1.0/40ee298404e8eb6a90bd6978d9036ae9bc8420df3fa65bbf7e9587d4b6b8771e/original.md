```
softmax_edge_neighbors(g, e)
```

Softmax over each node's neighborhood of the edge features `e`.

$$
\mathbf{e}'_{j\to i} = \frac{e^{\mathbf{e}_{j\to i}}}
                    {\sum_{j'\in N(i)} e^{\mathbf{e}_{j'\to i}}}.
$$
