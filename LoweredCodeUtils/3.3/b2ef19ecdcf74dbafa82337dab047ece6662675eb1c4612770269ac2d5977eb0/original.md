```
edges = CodeEdges(src::CodeInfo)
```

Analyze `src` and determine the chain of dependencies.

  * `edges.preds[i]` lists the preceding statements that statement `i` depends on.
  * `edges.succs[i]` lists the succeeding statements that depend on statement `i`.
  * `edges.byname[v]` returns information about the predecessors, successors, and assignment statements for an object `v::GlobalRef`.
