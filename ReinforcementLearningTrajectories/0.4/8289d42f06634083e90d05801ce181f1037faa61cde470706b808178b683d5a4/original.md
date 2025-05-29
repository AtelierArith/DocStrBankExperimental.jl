```
NormalizedTraces(traces::AbstractTraces, normalizers::NamedTuple)
NormalizedTraces(traces::AbstractTraces; trace_normalizer_pairs...)
```

Wraps an [`AbstractTraces`](@ref) and a `NamedTuple` of `Symbol` => [`Normalizer`](@ref)  pairs.  When pushing new elements to the traces, a `NormalizedTraces` will first update a running  estimate of the moments of traces present in the keys of `normalizers`. When sampling a normalized trace, it will first normalize the samples to zero mean and unit  variance. Traces that do not have a normalizer are sample as usual.

Note that when used in combination with [`Episodes`](@ref), `NormalizedTraces` must wrap  the `Episodes` struct, not the inner `AbstractTraces` contained in an `Episode`, otherwise  the running estimate will reset after each episode.

When used with a MultiplexTraces, the normalizer used with for one symbol (e.g. :state) will be the same used for the other one (e.g. :next_state).

Preconfigured normalizers are provided for scalar (see [`scalar_normalizer`](@ref)) and  arrays (see [`array_normalizer`](@ref)).

# Examples

```
t = CircularArraySARTSTraces(capacity = 10, state = Float64 => (5,))
nt = NormalizedTraces(t, reward = scalar_normalizer(), state = array_normalizer((5,)))
# :next_state will also be normalized. 
traj = Trajectory(
    container = nt,
    sampler = BatchSampler(10)
)
```
