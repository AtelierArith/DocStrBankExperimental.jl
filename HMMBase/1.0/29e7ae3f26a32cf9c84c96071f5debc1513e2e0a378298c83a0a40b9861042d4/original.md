```
gettransmat(seq; relabel = false) -> (Dict, Matrix)
```

Return the transition matrix associated to the label sequence `seq`.   The labels must be positive integer.  

**Arguments**

  * `seq::Vector{<:Integer}`: positive label sequence.

**Keyword Arguments**

  * `relabel::Bool = false`: if set to true the sequence will be made contiguous. E.g. `[7,7,9,9,1,1]` will become `[2,2,3,3,1,1]`.

**Output**

  * `Dict{Integer,Integer}`: the mapping between the original and the new labels.
  * `Matrix{Float64}`: the transition matrix.
