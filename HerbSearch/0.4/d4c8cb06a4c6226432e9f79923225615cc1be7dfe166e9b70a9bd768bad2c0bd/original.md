```
misclassification(results::AbstractVector{Tuple{<:Number,<:Number}})
```

Returns the amount of misclassified examples, i.e. how many tuples with non-matching entries are there in `results`.

# Arguments

  * `results<:AbstractVector{<:Tuple{Number,Number}}`: the vector of tuples, where each tuple is in the form `Tuple{expected_output, actual_output}`.
