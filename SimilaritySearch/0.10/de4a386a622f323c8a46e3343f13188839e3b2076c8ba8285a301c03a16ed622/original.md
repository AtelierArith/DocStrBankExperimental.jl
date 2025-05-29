```
index!(index::SearchGraph; parallel_block=get_parallel_block(), parallel_minimum_first_block=parallel_block, callbacks=SearchGraphCallbacks(verbose=index.verbose))
```

Indexes the already initialized database (e.g., given in the constructor method). It can be made in parallel or sequentially. The arguments are the same than `append!` function but using the internal `index.db` as input.
