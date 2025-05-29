```
vocab_reduction(wv::WordVectors, seed, nn)
```

Produces a reduced vocabulary version of `wv` by removing all but the `nn` nearest neighbors of each word present in the vocabulary `seed`.
