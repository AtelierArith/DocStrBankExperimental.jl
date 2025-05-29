```
(A::QuantumObjectEvolution)(ψout, ψin, p, t)
```

Apply the time-dependent [`QuantumObjectEvolution`](@ref) object `A` to the input state `ψin` at time `t` with parameters `p`. The output state is stored in `ψout`. This function mimics the behavior of a `AbstractSciMLOperator` object.

# Arguments

  * `ψout::QuantumObject`: The output state. It must have the same type as `ψin`.
  * `ψin::QuantumObject`: The input state. It must be either a [`Ket`](@ref) or a [`OperatorKet`](@ref).
  * `p`: The parameters of the time-dependent coefficients.
  * `t`: The time at which the coefficients are evaluated.

# Returns

  * `ψout::QuantumObject`: The output state.

# Examples

```jldoctest
julia> a = destroy(20)

Quantum Object:   type=Operator()   dims=[20]   size=(20, 20)   ishermitian=false
20×20 SparseMatrixCSC{ComplexF64, Int64} with 19 stored entries:
⎡⠈⠢⡀⠀⠀⠀⠀⠀⠀⠀⎤
⎢⠀⠀⠈⠢⡀⠀⠀⠀⠀⠀⎥
⎢⠀⠀⠀⠀⠈⠢⡀⠀⠀⠀⎥
⎢⠀⠀⠀⠀⠀⠀⠈⠢⡀⠀⎥
⎣⠀⠀⠀⠀⠀⠀⠀⠀⠈⠢⎦

julia> coef1(p, t) = sin(t)
coef1 (generic function with 1 method)

julia> coef2(p, t) = cos(t)
coef2 (generic function with 1 method)

julia> A = QobjEvo(((a, coef1), (a', coef2)))

Quantum Object Evo.:   type=Operator()   dims=[20]   size=(20, 20)   ishermitian=true   isconstant=false
(ScalarOperator(0.0 + 0.0im) * MatrixOperator(20 × 20) + ScalarOperator(0.0 + 0.0im) * MatrixOperator(20 × 20))

julia> ψ1 = fock(20, 3);

julia> ψ2 = zero_ket(20);

julia> A(ψ2, ψ1, nothing, 0.1) ≈ A(0.1) * ψ1
true
```
