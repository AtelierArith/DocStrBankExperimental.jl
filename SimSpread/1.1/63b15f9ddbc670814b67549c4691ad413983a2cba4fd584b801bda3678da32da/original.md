```
clean!(yhat::NamedArray, A::NamedArray, y::NamedArray)
```

Flag, in place, erroneous prediction from cross-validation splitting.

# Arguments

  * `yhat::NamedArray`: Predicted source-target bipartite adjacency matrix
  * `A::NamedArray`: Initial resource source-target resources adjacency matrix
  * `y::NamedArray`: Ground-truth source-target bipartite adjacency matrix
