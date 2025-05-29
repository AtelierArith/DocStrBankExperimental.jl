```
SimHistory
```

An (PO)MDP simulation history returned by `simulate(::HistoryRecorder, ::Union{MDP,POMDP},...)`.

This is an `AbstractVector` of [`NamedTuples`](https://docs.julialang.org/en/v1/manual/types/index.html#Named-Tuple-Types-1) containing the states, actions, etc.

# Examples

```
hist[1][:s] # returns the first state in the history
```

```
hist[:a] # returns all of the actions in the history
```
