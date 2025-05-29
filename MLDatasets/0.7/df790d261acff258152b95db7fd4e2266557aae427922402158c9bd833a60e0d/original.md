```
FileDataset([loadfn = FileIO.load,] paths)
FileDataset([loadfn = FileIO.load,] dir, pattern = "*", depth = 4)
```

Wrap a set of file `paths` as a dataset (traversed in the same order as `paths`). Alternatively, specify a `dir` and collect all paths that match a glob `pattern` (recursively globbing by `depth`). The glob order determines the traversal order.
