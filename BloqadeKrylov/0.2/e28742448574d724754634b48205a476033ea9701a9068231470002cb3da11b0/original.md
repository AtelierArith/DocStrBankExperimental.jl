```
struct Magnus4Evolution
Magnus4Evolution(reg::AbstractRegister, clocks, h; kw...)
```

Create a `Magnus4Evolution` object that describes a time evolution using Magnus method with 4th order.

# Arguments

  * `reg`: a register, should be a subtype of `AbstractRegister`.
  * `clocks`: the clocks of this time evolution at each step.
  * `h`: a hamiltonian expression.

# Keyword Arguments

  * `progress`: show progress bar, default is `false`.
  * `progress_name`: progress bar name, default is `"emulating"`.
  * `normalize_step`: normalize the state every `normalize_step`.
  * `normalize_finally`: wether normalize the state in the end of evolution, default is `true`.
  * `tol`: tolerance of the Krylov-expmv evaluation method, default is `1e-7`

# Examples

The following is the simplest way of using `Magnus4Evolution` via [`emulate!`](@ref). For more advanced usage, please refer to documentation page [Emulation](@ref emulation).

```jldoctest
julia> using Bloqade

julia> r = zero_state(5)
ArrayReg{2, ComplexF64, Array...}
    active qudits: 5/5
    nlevel: 2

julia> atoms = [(i, ) for i in 1:5]
5-element Vector{Tuple{Int64}}:
 (1,)
 (2,)
 (3,)
 (4,)
 (5,)

julia> h = rydberg_h(atoms; Ω=sin)
nqubits: 5
+
├─ [+] ∑ 5.42e6/|x_i-x_j|^6 n_i n_j
└─ [+] Ω(t) ⋅ ∑ σ^x_i


julia> prob = Magnus4Evolution(r, 0.0:1e-2:0.1, h);

julia> emulate!(prob); # run the emulation
```
