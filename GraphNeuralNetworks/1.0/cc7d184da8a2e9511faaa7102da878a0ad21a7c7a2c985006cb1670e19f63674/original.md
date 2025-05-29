```
Set2Set(n_in, n_iters, n_layers = 1)
```

Set2Set layer from the paper [Order Matters: Sequence to sequence for sets](https://arxiv.org/abs/1511.06391).

For each graph in the batch, the layer computes an output vector of size `2*n_in` by iterating the following steps `n_iters` times:

$$
\mathbf{q} = \mathrm{LSTM}(\mathbf{q}_{t-1}^*)
\alpha_{i} = \frac{\exp(\mathbf{q}^T \mathbf{x}_i)}{\sum_{j=1}^N \exp(\mathbf{q}^T \mathbf{x}_j)} 
\mathbf{r} = \sum_{i=1}^N \alpha_{i} \mathbf{x}_i
\mathbf{q}^*_t = [\mathbf{q}; \mathbf{r}]
$$

where `N` is the number of nodes in the graph, `LSTM` is a Long-Short-Term-Memory network with `n_layers` layers,  input size `2*n_in` and output size `n_in`.

Given a batch of graphs `g` and node features `x`, the layer returns a matrix of size `(2*n_in, n_graphs)`. ```
