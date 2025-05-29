```
choices::ChoiceMap = from_array(proto_choices::ChoiceMap, arr::Vector)
```

Return an assignment with the same address structure as a prototype assignment, but with values read off from the given array.

The order in which addresses are populated is determined by the prototype assignment. It is an error if the number of choices in the prototype assignment is not equal to the length the array.

# Implementation

To support `from_array`, a concrete subtype `T <: ChoiceMap` should implement the following method:

```
(n::Int, choices::T) = _from_array(proto_choices::T, arr::Vector{V}, start_idx::Int) where {V}
```

Return an assignment with the same address structure as a prototype assignment, but with values read off from `arr`, starting at position `start_idx`, and the number of elements read from `arr`.
