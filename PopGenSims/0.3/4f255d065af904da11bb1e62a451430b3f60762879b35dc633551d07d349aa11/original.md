```
cross(data::PopData, parent1::String, parent2::String; n::Int = 100, generation::String = "F1")
```

Simulate a breeding cross between individuals `parent1` and `parent2` from a `PopData` object. Returns PopData consisting of `n` offspring resulting from the cross.

#### Keyword Arguments

  * `n` : Integer of number of offspring to generate (default: `100`)
  * `generation` : A string to assign `population` identity to the offspring (default: `"F1"`)
