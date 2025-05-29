```
Circuit(v)
```

Construct a `Circuit` from a `Vector`-like `v` containing tuples of:

  * a [`Gate`](@ref), [`Noise`](@ref), or [`Result`](@ref)
  * the target qubits on which to apply the operator
  * any construction arguments to the operator, e.g. an angle or [`Observable`](@ref Braket.Observables.Observable)

# Examples

```jldoctest
julia> v = [(H, collect(0:10)), (Rx, 1, 0.2), (BitFlip, 0, 0.1)];

julia> Circuit(v);
```
