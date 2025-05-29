```
PointVariableRef <: FiniteRef
```

A `DataType` for variables defined at a transcipted point (e.g., second stage variable at a particular scenario, dynamic variable at a discretized time point).

**Fields**

  * `model::InfiniteModel`: Infinite model.
  * `index::PointVariableIndex`: Index of the variable in model.
