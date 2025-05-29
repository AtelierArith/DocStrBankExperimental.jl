```
isdigraphical(indegree_sequence, outdegree_sequence)
```

Check whether the given indegree sequence and outdegree sequence are digraphical, that is whether they can be the indegree and outdegree sequence of a simple digraph (i.e. a directed graph with no loops). This implies that `indegree_sequence` and `outdegree_sequence` are not independent, as their elements respectively represent the indegrees and outdegrees that the vertices shall have.

### Implementation Notes

According to Fulkerson-Chen-Anstee theorem, a sequence $\{(a_1, b_1), ...,(a_n, b_n)\}$ (sorted in descending order of a) is graphic iff $\sum_{i = 1}^{n} a_i = \sum_{i = 1}^{n} b_i\}$ and the sequence obeys the property -

$$
\sum_{i=1}^{r} a_i \leq \sum_{i=1}^n min(r-1,b_i) + \sum_{i=r+1}^n min(r,b_i)
$$

for each integer 1 <= r <= n-1. 

See also: [`isgraphical`](@ref)
