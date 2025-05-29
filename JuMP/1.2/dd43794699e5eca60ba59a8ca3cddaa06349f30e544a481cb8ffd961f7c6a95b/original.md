```
node_count(model::Model)
```

Gets the total number of branch-and-bound nodes explored during the most recent optimization in a Mixed Integer Program.

Solvers must implement `MOI.NodeCount()` to use this function.
