`optimize(hamiltonian::Hamiltonian, basisset::GeometricBasisSet; perturbation=Hamiltonian(), info=4, optimizer=Optim.NelderMead())`

This function minimizes the energy by optimizing $r_1$ and $r_n$ using Optim.jl.

$$
\frac{\partial E}{\partial r_1} = \frac{\partial E}{\partial r_n} = 0
$$
