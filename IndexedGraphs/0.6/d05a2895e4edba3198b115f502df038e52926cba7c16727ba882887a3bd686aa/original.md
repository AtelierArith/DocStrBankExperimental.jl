```
bidirected_with_mappings(g::IndexedGraph) -> (gdir, dir2undir, undir2dir)
```

Construct an `IndexedBiDiGraph` `gdir` from an `IndexedGraph` `g` by building two directed edges per every undirected edge in `g`. In addition, return two vectors containing mappings from the undirected edges of `g` to the corresponding directed edges of `gdir`.

### OUTPUT

  * `gdir` – The directed graph
  * `dir2undir` – A vector of integers mapping the indices of the directed edges of `gdir` to the corresponding undirected edges of `g`
  * `undir2dir` – A vector of vectors with two integers each mapping the indices of the undirected edges of `g` to the two corresponding directed edges of `gdir`
