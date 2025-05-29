Function to build the transverse field Ising model hamiltonian at a given unitless timestep `s`.

Arguments: ising*model - ising model represented as a dictionary.  The qubits               and couplings are represented as tuples, and the weights               are numbers.               For Example: im = Dict((1,) => 1, (2,) => 0.5, (1,2) => 2) annealing*schedule - The annealing schedule, of the form given by the struct s - the imaginary timestep. This should usually be in the range from 0.0-to-1.0
