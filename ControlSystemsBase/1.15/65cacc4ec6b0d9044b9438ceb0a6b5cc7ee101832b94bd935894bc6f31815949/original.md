`sysr, G, T = balreal(sys::StateSpace)`

Calculates a balanced realization of the system sys, such that the observability and reachability gramians of the balanced system are equal and diagonal `diagm(G)`. `T` is the similarity transform between the old state `x` and the new state `z` such that `z = Tx`.

See also [`gram`](@ref), [`baltrunc`](@ref).

Reference: Varga A., Balancing-free square-root algorithm for computing singular perturbation approximations.
