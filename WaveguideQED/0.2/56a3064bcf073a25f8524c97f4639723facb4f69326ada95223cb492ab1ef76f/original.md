```
detect_single_click(ψ,detector::Detector,projection)
detect_single_click(ψ,detector::Detector)
```

Calculate probability of observing `projection` after beamsplitter operation and subsequent detection event defined in `detector` on the state `ψ`.

# Arguments

  * `ψ` can be either [`LazyTensorKet`](@ref) or [`LazySumKet`](@ref) and is the state on which the beamsplitter and detection is applied
  * `detector` defines the beamsplitter and subsequent detection operation. See [`Detector`](@ref) for more details on how to define.
  * `projection` if given is a [`LazyTensorKet`](@ref) or [`LazySumKet`](@ref) which projects onto the state after the measurement.  If no projection is given, instead the total probability of having the detector click is given by applying all possible combinations of projections using [`get_all_projectors`](@ref).

# Returns

  * If `projection` is given returns probability of having detector click and being in state defined by `projection`
  * If `projection` is not given returns the total probability of having a the detector click (only a single click, for double clicks use [`detect_double_click`](@ref)) by applying all possibile projections with zerophotons in the waveguide using [`get_all_projectors`](@ref).

See [Beamsplitter](https://mabuni1998.github.io/WaveguideQED/dev/detection_example/) for an example on how to use.
