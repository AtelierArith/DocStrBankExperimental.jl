`optimize(hamiltonian::Hamiltonian, basis::Basis; perturbation=Hamiltonian(), info=4, optimizer=Optim.NelderMead())`

これは1基底計算のための最適化器です。この関数は `optimize(hamiltonian, BasisSet(basis); perturbation=perturbation, info=info, progress=progress, optimizer=optimizer, options...)` を返します。
