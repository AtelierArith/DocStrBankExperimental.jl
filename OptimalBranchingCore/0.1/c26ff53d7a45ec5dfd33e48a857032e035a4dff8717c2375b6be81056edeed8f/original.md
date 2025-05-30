```
BranchingTable{INT <: Integer}
```

A list of groupped bitstrings, which is used for designing the branching rule. A valid branching rule, which is represented by a logic expression in Disjunctive Normal Form (DNF), should cover at least one bitstring from each group, where by `cover`, we mean there exists at least one bitstring in the group that satisfies the logic expression. Please check [`covered_by`](@ref) for more details.

### Fields

  * `bit_length::Int`: The length of the bit string.
  * `table::Vector{Vector{INT}}`: The list of groupped bitstrings used for branching, where each group is a vector of bitstrings. The bitstrings uses `INT` type to store the bitstring.
