```
mutable struct MISProblem{INT <: Integer} <: AbstractProblem
```

Represents a Maximum Independent Set (MIS) problem.

# Fields

  * `g::SimpleGraph`: The graph associated with the MIS problem.

# Methods

  * `copy(p::MISProblem)`: Creates a copy of the given `MISProblem`.
  * `Base.show(io::IO, p::MISProblem)`: Displays the number of vertices in the `MISProblem`.
