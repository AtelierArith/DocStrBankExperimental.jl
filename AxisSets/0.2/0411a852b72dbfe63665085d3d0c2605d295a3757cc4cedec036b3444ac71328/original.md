```
KeyedDataset
```

A `KeyedDataset` describes an associative collection of component `KeyedArray`s with constraints on their shared dimensions.

# Fields

  * `constraints::OrderedSet{Pattern}` - Constraint [`Pattern`](@ref)s on shared dimensions.
  * `data::LittleDict{Tuple, KeyedArray}` - Flattened key paths as tuples component keyed arrays.
