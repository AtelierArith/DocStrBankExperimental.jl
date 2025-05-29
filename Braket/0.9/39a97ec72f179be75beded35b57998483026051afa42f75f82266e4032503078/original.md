```
AdjointGradient(o::Observable, targets, parameters::Vector) -> AdjointGradient
AdjointGradient(o::Observable, targets) -> AdjointGradient
```

Constructs an `AdjointGradient` with respect to the expectation value of an observable `o` on qubits `targets`. The gradient will be calculated by computing partial derivatives with respect to `parameters`. If `parameters` is not present, is empty, or is `["all"]`, all parameters in the circuit will be used. 

`targets` may be one of:

  * A [`QubitSet`](@ref)
  * A `Vector` of `Int`s and/or [`Qubit`](@ref)s
  * An `Int` or `Qubit`

`AdjointGradient` supports using [`Sum`](@ref) observables. If `o` is a `Sum`, `targets` should be a nested vector of target qubits, such that the `n`-th term of `targets` has the same length as the `n`-th term of `o`.

# Examples

```jldoctest
julia> α = FreeParameter(:alpha);

julia> c = Circuit([(H, 0), (H, 1), (Rx, 0, α), (Rx, 1, α)]);

julia> op = 2.0 * Braket.Observables.X() * Braket.Observables.X();

julia> c = AdjointGradient(c, op, [QubitSet(0, 1)], [α]);
```

Using a `Sum`:

```jldoctest
julia> α = FreeParameter(:alpha);

julia> c = Circuit([(H, 0), (H, 1), (Rx, 0, α), (Rx, 1, α)]);

julia> op1 = 2.0 * Braket.Observables.X() * Braket.Observables.X();

julia> op2 = -3.0 * Braket.Observables.Y() * Braket.Observables.Y();

julia> c = AdjointGradient(c, op1 + op2, [QubitSet(0, 1), QubitSet(0, 2)], [α]);
```
