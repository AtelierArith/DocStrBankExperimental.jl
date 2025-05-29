`solve(hamiltonian::Hamiltonian, basisset::BasisSet)`

This function returns the eigenvalues $E$  and eigenvectors $\pmb{c}$ for

$$
\pmb{H} \pmb{c} = E \pmb{S} \pmb{c}.
$$

The Hamiltonian matrix is defined as $H_{ij} = \langle \phi_{i} | \hat{H} | \phi_{j} \rangle$. The overlap matrix is defined as $S_{ij} = \langle \phi_{i} | \phi_{j} \rangle$.
