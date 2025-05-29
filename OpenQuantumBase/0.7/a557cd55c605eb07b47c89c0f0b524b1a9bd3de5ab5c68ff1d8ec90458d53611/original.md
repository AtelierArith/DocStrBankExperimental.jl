```julia
project_to_lowlevel(
    H,
    s_axis,
    coupling,
    dH;
    lvl,
    digits,
    direction,
    refs
)

```

Project a Hamiltonian `H` to the lowest `lvl` level subspace. `s_axis` is the grid of (unitless) times on which the projection is calculated. `dH` is the derivative of the Hamiltonian. `coupling` is the system-bath interaction operator. Both of `coupling` and `dH` should be callable with annealing parameter `s`. `atol` and `rtol` are the absolute and relative error tolerance to distinguish two degenerate energy levels. `direction`, which can be either `:forward` or `backward`, controls whether to start the calcuation from the starting point or the end point. Currently this function only support real Hamiltonian with non-degenerate energies.
