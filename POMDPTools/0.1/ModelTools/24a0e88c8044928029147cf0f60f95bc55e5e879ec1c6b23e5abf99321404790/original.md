```
reward_vector(p::SparseTabularProblem, a)
```

Accessor function for the reward function of a sparse tabular problem. It returns a vector containing the reward for all the states when taking action a: R(s, a).  The length of the return vector is equal to the number of states.
