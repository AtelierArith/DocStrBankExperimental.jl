```
SemiInfiniteVariableRef <: DispatchVariableRef
```

A `DataType` for partially transcripted infinite dimensional variable references. This is used to expand measures that contain infinite variables that are not fully transcripted by the measure.

**Fields**

  * `model::InfiniteModel`: Infinite model.
  * `index::SemiInfiniteVariableIndex`: Index of the variable in model.
