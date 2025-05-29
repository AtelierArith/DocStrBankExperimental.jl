```
karger_min_cut(g)
```

Perform [Karger Minimum Cut](https://en.wikipedia.org/wiki/Karger%27s_algorithm) to find the minimum cut of graph `g` with some probability of success. A cut is a partition of `vertices(g)` into two non-empty sets. The size of a cut is the number of edges crossing the two non-empty sets. 

### Implementation Notes

The cut is represented by an integer array. If `cut[v] == 1` then `v` is in the first non-empty set. If `cut[v] == 2` then `v` is in the second non-empty set. `cut[1] = 1`.

If |V| < 2 then `cut[v] = 0` for all `v`.

### Performance

Runtime: O(|E|) Memory: O(|E|)
