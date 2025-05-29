```julia
setSolvableOldPoses!(
    dfg;
    youngest,
    oldest,
    solvable,
    filterLabel
)

```

Set old poses and adjacent factors to `solvable::Int=0` (default).

Notes

  * `youngest::Int` and `oldest::Int` set the limits of search by count,

      * `oldest` set large enough for solver loop defintely disengage old parts in re-occuring cycle.
  * `filterLabel::Regex` sets the template to search for each pose label.
  * Poses are assumed to be a thread through time that connects the local exploration variables.
  * Initially developed to remove old variables and factors from a solution, in combination with fix-lag marginalization.

      * `getSolverParams(fg).isfixedlag=true`

Related:

getLastPoses
