```
DNF{INT}
```

A data structure representing a logic expression in Disjunctive Normal Form (DNF), which is a disjunction of one or more conjunctions of literals. In OptimalBranchingCore, a DNF is used to represent the branching rule.

# Fields

  * `clauses::Vector{Clause{INT}}`: A vector of `Clause` objects.
