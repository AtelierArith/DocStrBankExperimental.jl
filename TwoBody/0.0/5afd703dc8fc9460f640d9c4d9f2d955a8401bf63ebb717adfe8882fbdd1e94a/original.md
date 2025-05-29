`solve(hamiltonian::Hamiltonian, method::FiniteDifferenceMethod; perturbation=Hamiltonian(), info=4, nₘₐₓ=4)`

This method solve the eigenvalue problem for the Hamiltonian discretized as a sparse matrix with finite difference approximation,

$$
\pmb{H} \pmb{\psi} = E \pmb{\psi}.
$$

The eigenvalue $E$ is an approximation of the exact energy and the eigenvector $\pmb{\psi}$ is a vector of the approximated values of the exact wavefunction $\psi(r)$ on points of the grid,

$$
\pmb{\psi}
=
\left(\begin{array}{c}
  \psi(r_1) \\
  \psi(r_2) \\
  \psi(r_3) \\
  \vdots \\
\end{array}\right).
$$
