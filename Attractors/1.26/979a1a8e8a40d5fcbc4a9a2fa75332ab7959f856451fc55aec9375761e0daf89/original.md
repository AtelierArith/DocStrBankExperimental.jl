```
EdgeTrackingResults(edge, track1, track2, time, bisect_idx)
```

Data type that stores output of the [`edgetracking`](@ref) algorithm.

## Fields

  * `edge::StateSpaceSet`: the pseudo-trajectory representing the tracked edge segment (given by the average in state space between `track1` and `track2`)
  * `track1::StateSpaceSet`: the pseudo-trajectory tracking the edge within basin 1
  * `track2::StateSpaceSet`: the pseudo-trajectory tracking the edge within basin 2
  * `time::Vector`: time points of the above `StateSpaceSet`s
  * `bisect_idx::Vector`: indices of `time` at which a re-bisection occurred
  * `success::Bool`: indicates whether the edge tracking has been successful or not
