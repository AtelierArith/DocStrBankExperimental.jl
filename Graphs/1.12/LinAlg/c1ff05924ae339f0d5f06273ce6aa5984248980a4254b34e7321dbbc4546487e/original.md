```
non_backtracking_matrix(g)
```

Return a non-backtracking matrix `B` and an edgemap storing the oriented edges' positions in `B`.

Given two arcs $A_{i j}` and `A_{k l}` in `g`, the non-backtracking matrix$B`` is defined as

$B_{A_{i j}, A_{k l}} = δ_{j k} * (1 - δ_{i l})$
