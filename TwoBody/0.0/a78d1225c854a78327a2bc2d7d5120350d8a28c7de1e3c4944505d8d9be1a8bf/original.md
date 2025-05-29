`function optimize(hamiltonian::Hamiltonian, basisset::BasisSet; perturbation=Hamiltonian(), info=4, progress=true, optimizer=Optim.NelderMead(), options...)`

This function minimizes the energy by changing the exponents of the basis functions using Optim.jl.

$$
\frac{\partial E}{\partial a_i} = 0
$$
