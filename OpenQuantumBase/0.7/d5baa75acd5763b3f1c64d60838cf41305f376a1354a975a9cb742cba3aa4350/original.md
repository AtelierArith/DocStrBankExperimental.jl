```julia
DiffEqLiouvillian(
    H,
    opensys_eig,
    opensys,
    lvl;
    digits,
    sigdigits
)

```

The constructor of the `DiffEqLiouvillian` type. `opensys_eig` is a list of  open-system Liouvillians that which require diagonalization of the Hamiltonian. `opensys` is a list of open-system Liouvillians which does not require  diagonalization of the Hamiltonian. `lvl` is the truncation levels of the energy eigenbasis if the method supports the truncation.
