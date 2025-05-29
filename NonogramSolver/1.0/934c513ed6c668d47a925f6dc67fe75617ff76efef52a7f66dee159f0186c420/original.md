Holds JuMP's termination status after a solution attempt, and the solution itself if successful.

# Fields

  * `jumpTerminationStatus`: the eventual output of `JuMP.termination_status`, indicating the outcome of the solution attempt.
  * `z::Matrix{T}`: Spatial array of cell colors (of type `T`) in solution, if successful.
  * `palette::P`: Collection of possible cell colors (each of type `T`). Does not include lack of color, which is indicated as `zero(T)`.
