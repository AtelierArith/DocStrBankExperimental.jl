```
centrality_closeness(N::UnipartiteNetwork; nmax::Int64=20)
```

The function calls `shortest_path` internally – the `nmax` argument is the maximal path length that will be tried.

#### References

  * Bavelas, A., 1950. Communication Patterns in Task‐Oriented Groups. The Journal of the Acoustical Society of America 22, 725–730. doi:10.1121/1.1906679
