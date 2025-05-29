```
cross(parent_1::Pair, parent_2::Pair, n::Int = 100, generation::String = "F1")
```

Simulate a breeding cross between individuals `parent` and `parent2` from two different `PopData` objects. Returns PopData consisting of `n` offspring resulting from the cross. `parent_1_data` and `parent_2_data`  are positional arguments, therefore they must be written without keywords and in the order of parents 1, parent 2. 

#### Keyword Arguments

  * `parent_1` : Pair of `PopData => "Parent1Name"`
  * `parent_2` : Pair of `PopData => "Parent1Name"`
  * `n` : Integer of number of offspring to generate (default: `100`)
  * `generation` : A string to assign `population` identity and name prefix to the offspring (default: `"F1"`)
