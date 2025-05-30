```
observation_matrix(p::SparseTabularPOMDP, a::Int64)
```

Accessor function for the observation model of a sparse tabular POMDP. It returns a sparse matrix containing the observation probabilities when having taken action a: O[sp, o] = Pr(o | sp, a).
