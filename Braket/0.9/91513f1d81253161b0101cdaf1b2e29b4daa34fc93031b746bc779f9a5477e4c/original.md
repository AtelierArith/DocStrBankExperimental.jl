```
AdjointGradient(c::Circuit, o::Observable, targets, parameters) -> Circuit
```

Constructs an `AdjointGradient` computation with respect to the expectation value of an observable `o` on qubits `targets`, computing partial derivatives of `parameters`, and adds it as a result to [`Circuit`](@ref) `c`.

`o` may be any `Observable`. `targets` must be a `Vector` of `QubitSet`s (or a single `QubitSet`, if `o` is not a `Sum`), each of which is the same length as the qubit count of the corresponding term in `o`. `parameters` can have elements which are [`FreeParameter`](@ref)s or `String`s, or `["all"]`, in which case the gradient is computed with respect to all parameters in the circuit.

# Examples

```jldoctest
julia> c = Circuit();

julia> α = FreeParameter("alpha");

julia> c = H(c, collect(0:10));

julia> c = Rx(c, collect(0:10), α);

julia> c = AdjointGradient(c, Braket.Observables.Z(), 0, [α]);
```
