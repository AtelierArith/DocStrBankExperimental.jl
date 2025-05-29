```
detect_double_click(ψ,detector1,detector2,projection)
detect_double_click(ψ,detector1,detector2)
```

Calculate probability of observing `projection` after beamsplitter operation and two subsequent detection events defined in `detector1` and `detector2` on the state `ψ`.

# Arguments

  * `ψ` can be either [`LazyTensorKet`](@ref) or [`LazySumKet`](@ref) and is the state on which the beamsplitter and detection is applied
  * `detector1` defines the first beamsplitter and subsequent detection operation. See [`Detector`](@ref) for more details on how to define.
  * `detector2` defines the second beamsplitter and subsequent detection operation. See [`Detector`](@ref) for more details on how to define.
  * `projection` if given is a [`LazyTensorKet`](@ref) or [`LazySumKet`](@ref) which projects onto the state after the measurement.  If no projection is given, instead the total probability of having the detector click is given by applying all possible combinations of projections using [`get_all_projectors`](@ref).

# Returns

  * If `projection` is given: Returns probability of having `detector1` and `detector2` click and being in state defined by `projection`
  * If `projection` is not given: Returns the total probability of having `detector1` and `detector2` click by applying all possibile projections with zerophotons in the waveguide using [`get_all_projectors`](@ref).

See [Beamsplitter](https://mabuni1998.github.io/WaveguideQED/dev/detection_example/) for an example on how to use. 
