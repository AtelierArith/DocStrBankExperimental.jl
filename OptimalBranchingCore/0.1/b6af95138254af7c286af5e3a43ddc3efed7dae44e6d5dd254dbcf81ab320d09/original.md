```
Clause{INT <: Integer}
```

A Clause is conjunction of literals, which is specified by a pair of bit strings. The type parameter `INT` is the integer type for storing the bit strings.

### Fields

  * `mask`: A bit string that indicates the variables involved in the clause.
  * `val`: A bit string that indicates the positive literals in the clause.

### Examples

To check if a bit string satisfies a clause, use `OptimalBranchingCore.covered_by`.

```jldoctest
julia> using OptimalBranchingCore

julia> clause = Clause(0b1110, 0b1010)
Clause{UInt8}: #2 ∧ ¬#3 ∧ #4

julia> OptimalBranchingCore.covered_by(0b1110, clause)
false

julia> OptimalBranchingCore.covered_by(0b1010, clause)
true
```
