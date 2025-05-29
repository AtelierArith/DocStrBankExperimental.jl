Computation of δᵥ

This function computes the angle δᵥ based on the given parameters.

Arguments:

  * ::TestRound: The test round object.
  * ::DummyQubit: The dummy qubit object.
  * θᵥ: The input angle.

Returns:

  * δᵥ: The computed angle δᵥ.

Case:

1. Round ≡ Test ∩ Qubit ≡ Dummy  → δᵥ = {kπ/r | k ∼ U(0..7)}

# Examples

```julia
julia> compute_angle_δᵥ(TestRound(),DummyQubit(),0)
0
```
