```
indexed_meanfield(ops::Vector,H::QNumber,J::Vector;
    Jdagger::Vector=adjoint.(J),rates=ones(length(J)))
```

Compute the set of equations for the indexed-operators [`IndexedOperator`](@ref) in `ops` under the Hamiltonian `H` and with loss operators contained in `J`. The resulting equation is equivalent to the Quantum-Langevin equation where noise is neglected. This is a modified version of the [`meanfield`](@ref) function, that can now also take [`IndexedOperator`](@ref) entities for both the `ops` argument aswell as for the `J` arguments. See also: [`meanfield`](@ref).

# Arguments

*`ops::Vector`: The operators of which the equations are to be computed. *`H::QNumber`: The Hamiltonian describing the reversible dynamics of the     system. *`J::Vector{<:QNumber}`: A vector containing the collapse operators of     the system. A term of the form     $\sum_i J_i^\dagger O J_i - \frac{1}{2}\left(J_i^\dagger J_i O + OJ_i^\dagger J_i\right)$     is added to the Heisenberg equation.

# Optional argumentes

*`Jdagger::Vector=adjoint.(J)`: Vector containing the hermitian conjugates of     the collapse operators. *`rates=ones(length(J))`: Decay rates corresponding to the collapse operators in `J`. *`multithread=false`: Specify whether the derivation of equations for all operators in `ops`     should be multithreaded using `Threads.@threads`. *`simplify=true`: Specify whether the derived equations should be simplified. *`order=nothing`: Specify to which `order` a [`cumulant_expansion`](@ref) is performed.     If `nothing`, this step is skipped. *`mix_choice=maximum`: If the provided `order` is a `Vector`, `mix_choice` determines     which `order` to prefer on terms that act on multiple Hilbert spaces. *`iv=ModelingToolkit.t`: The independent variable (time parameter) of the system.
