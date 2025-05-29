```
HallOfFame{T<:DATA_TYPE,L<:LOSS_TYPE}
```

List of the best members seen all time in `.members`, with `.members[c]` being the best member seen at complexity c. Including only the members which actually have been set, you can run `.members[exists]`.

# Fields

  * `members::Array{PopMember{T,L},1}`: List of the best members seen all time.   These are ordered by complexity, with `.members[1]` the member with complexity 1.
  * `exists::Array{Bool,1}`: Whether the member at the given complexity has been set.
