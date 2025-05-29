```
guesswork_MISDP(
    p::AbstractVector{T},
    ρBs::AbstractVector{<:AbstractMatrix},
    num_outcomes = size(ρBs[1], 1)^2;
    solver,
    c = T.(1:length(p)),
    verbose::Bool = true,
) where {T<:Number} -> NamedTuple
```

Computes an approximation to the guesswork with `num_outcomes` possible guessing orders for the c-q state specified by a probability vector `p`, giving the distribution `X`, and `ρBs`, giving the associated quantum states. If $num_outcomes ≥ d_B^2$, where `d_B` is the dimension of the Hilbert space on which the quantum states live, then this computes exactly the guesswork. Note that one may not supply a parameter `K` in this case; in the mixed-integer SDP formulation, the guesser is always allowed to make `length(p)` guesses. However, a custom cost vector `c` may be supplied to choose how to penalize each possible number of guesses required to get the correct answer.

The size of the mixed-integer SDP solved by this function grows polynomially in `length(p)`, the dimension `d_B`, and `num_outcomes`, but mixed-integer SDPs are not known to be efficiently computable in general.

The keyword argument `solver` must be supplied with a solver capable of solving mixed-integer SDPs. Currently, this means [Pajarito.jl](https://github.com/JuliaOpt/Pajarito.jl) which solves mixed-integer SDPs by solving an alternating sequence of mixed-integer linear programs and SDPs. See the documentation for an example. Note that the performance of Pajarito depends on the performance of the underlying mixed-integer linear solver and SDP solver it is given, and that commerical solvers often have academic licenses and can be much more performant.

The keyword argument `verbose` prints the status, optimal value, optimal guessing orders, and POVMs, in addition to warnings from Convex.jl if the problem is not optimally solved.
