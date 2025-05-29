```
arr::Vector{T} = to_array(choices::ChoiceMap, ::Type{T}) where {T}
```

Populate an array with values of choices in the given assignment.

It is an error if each of the values cannot be coerced into a value of the given type.

# Implementation

To support `to_array`, a concrete subtype `T <: ChoiceMap` should implement the following method:

```
n::Int = _fill_array!(choices::T, arr::Vector{V}, start_idx::Int) where {V}
```

Populate `arr` with values from the given assignment, starting at `start_idx`, and return the number of elements in `arr` that were populated.
