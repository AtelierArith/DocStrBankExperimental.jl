```
XPRSloaddirs(prob, ndirs, colind, priority, dir, uppseudo, downpseudo)::prob
```

Loads directives into the matrix.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `ndirs::Integer`: Number of directives.
  * `colind::AbstractVector{Integer}`: Integer array of length `ndirs` containing the column numbers.
  * `priority::AbstractVector{Integer}`: Integer array of length `ndirs` containing the priorities for the columns or sets.
  * `dir::AbstractVector{Cchar}`: Character array of length `ndirs` specifying the branching direction for each column or set: Uthe entity is to be forced up; Dthe entity is to be forced down; Nnot specified.May be `nothing` if not required.
  * `uppseudo::AbstractVector{Number}`: Double array of length `ndirs` containing the up pseudo costs for the columns or sets.
  * `downpseudo::AbstractVector{Number}`: Double array of length `ndirs` containing the down pseudo costs for the columns or sets.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSloaddirs](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSloaddirs.html) in the C API.
