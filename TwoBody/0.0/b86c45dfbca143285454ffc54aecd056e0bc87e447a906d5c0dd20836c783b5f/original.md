`optimize(hamiltonian::Hamiltonian, basis::Basis; perturbation=Hamiltonian(), info=4, optimizer=Optim.NelderMead())`

This a optimizer for 1-basis calculations. This function returns `optimize(hamiltonian, BasisSet(basis); perturbation=perturbation, info=info, progress=progress, optimizer=optimizer, options...)`.
