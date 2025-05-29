```
random_walk_pe(g, walk_length)
```

Return the random walk positional encoding from the paper [Graph Neural Networks with Learnable Structural and Positional Representations](https://arxiv.org/abs/2110.07875) of the given graph `g` and the length of the walk `walk_length` as a matrix of size `(walk_length, g.num_nodes)`. 
