```
j1_j2_model([elt::Type{T}, symm::Type{S},] lattice::InfiniteSquare;
            J1=1.0, J2=1.0, spin=1//2, sublattice=true)
```

Square lattice $J_1\text{-}J_2$ model, defined by the Hamiltonian

$$
H = J_1 \sum_{\langle i,j \rangle} \vec{S}_i \cdot \vec{S}_j
+ J_2 \sum_{\langle\langle i,j \rangle\rangle} \vec{S}_i \cdot \vec{S}_j,
$$

where $\vec{S}_i = (S_i^x, S_i^y, S_i^z)$. We denote the nearest and next-nearest neighbor terms using $\langle i,j \rangle$ and $\langle\langle i,j \rangle\rangle$, respectively. The `sublattice` kwarg enables a single-site unit cell ground state via a unitary sublattice rotation.
