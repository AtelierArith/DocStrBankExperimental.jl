```
bulksearch(ss, queries, t::SearchType [, skip]; kwargs... ) → vec_of_idxs, vec_of_ds
```

Same as [`search`](@ref) but many searches are done for many input query points.

In this case `skip` takes two arguments `skip(i, j)` where now `j` is simply the index of the query that we are currently searching for (`j` is the index in `queries` and goes from 1 to `length(queries)`).
