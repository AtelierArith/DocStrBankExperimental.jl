```
evolve_generator(H, L[, localH][, ω])
```

Create the generator for the evolution superoperator. Given Hamiltonian `H`, collection of Lindblad operator `L`, local Hamiltonian `localH` and scaling parameter `ω`, the generator is obtained as a sum

$-i(1-ω) (H ⊗ 1 - 1 ⊗ H) + ω (-i(localH ⊗ 1 - 1 ⊗ localH) + ∑(L ⊗ L̄ - 1/2(L^†L ⊗ 1 + 1 ⊗ L^T L̄ )))$

The last two arguments are optional.

If `localH` is not given, it defaults to sparse zero matrix of the size of `H`.

If `ω` is not given, both parts are taken with the same intensity and the global operator takes the form

$-i(H ⊗ 1 - 1 ⊗ H) + (-i(localH ⊗ 1 - 1 ⊗ localH) + ∑(L ⊗ L̄ - 1/2(L^†L ⊗ 1 + 1 ⊗ L^T L̄ )))$

# Arguments

  * `H`: Hamiltonian, must be hermitian,
  * `L`: collection of Lindblad operators, each must be of the same size as `H`,
  * `localH`: local Hamiltonian, suggested for nonmoralized QS walk, must be hermitian and of the size of `H`,
  * `ω`: scaling parameter, should be in [0, 1].

# Return

The generator matrix, which can be used in `evolve` function.

# Examples

```jldoctest; setup = :(using QSWalk)
julia> H, L, localH = [0 1+im; 1-im 0], [0. 1; 0 0], [1. 0.; 0. 1.]
(Complex{Int64}[0 + 0im 1 + 1im; 1 - 1im 0 + 0im], [0.0 1.0; 0.0 0.0], [1.0 0.0; 0.0 1.0])

julia> evolve_generator(H, [L], localH, 1/2)
4×4 Array{Complex{Float64},2}:
  0.0+0.0im    0.5+0.5im    0.5-0.5im   0.5+0.0im
 -0.5+0.5im  -0.25+0.0im    0.0+0.0im   0.5-0.5im
 -0.5-0.5im    0.0+0.0im  -0.25+0.0im   0.5+0.5im
  0.0+0.0im   -0.5-0.5im   -0.5+0.5im  -0.5+0.0im

```
