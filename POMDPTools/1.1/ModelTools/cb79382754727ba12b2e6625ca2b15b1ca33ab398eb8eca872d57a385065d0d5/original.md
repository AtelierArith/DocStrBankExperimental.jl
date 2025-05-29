```
transition_matrix(p::SparseTabularProblem, a)
```

Accessor function for the transition model of a sparse tabular problem. It returns a sparse matrix containing the transition probabilities when taking action a: T[s, sp] = Pr(sp | s, a).
