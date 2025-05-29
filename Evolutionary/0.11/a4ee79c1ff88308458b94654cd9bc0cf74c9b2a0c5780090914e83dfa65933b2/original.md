```
BSX(k::Int)
```

Binary Subset Crossover[^7]. Produces an offspring by first pooling the unique items of the two parents, and then creating each offspring by sampling without  replacement at most `k` elements from the pool of items.
