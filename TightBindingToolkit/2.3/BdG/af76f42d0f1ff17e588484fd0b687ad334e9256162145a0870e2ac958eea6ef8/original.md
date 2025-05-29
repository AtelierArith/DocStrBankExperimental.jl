```julia
FindFilling(M::BdGModel) --> Float64
FindFilling(mu::Float64, M::BdGModel)
```

Find filling at given temperature and chemical potential that takes BdGModel object as argument instead of Hamiltonian, since for a BdG case, the filling depends on the wavefunctions also. Because of this, if you want to calculate the filling at a different chemical potential, you have to modify the Hamiltonian, the UnitCells, rediagonalize, and recalculate eveyrthing.
