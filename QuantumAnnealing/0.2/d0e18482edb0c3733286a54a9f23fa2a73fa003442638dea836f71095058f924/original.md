simulator that uses the DifferentialEquations.jl differential equation solver to solve the Schrodinger Equation, rather than the Magnus Expansion.  This simulator can run into issues at higher anneal times.  The API is the same as for the simulate function.

Arguments: ising*model - ising model represented as a dictionary.  The qubits               and couplings are represented as tuples, and the weights               are numbers.               For Example: im = Dict((1,) => 1, (2,) => 0.5, (1,2) => 2) annealing*schedule - The annealing schedule, of the form given by the struct reltol - the relative tolerance that will be used in the ODE simulation

Parameters: initial*state - Initial state vector. Defaults to uniform superposition state on n qubits constant*field*x - vector of constant biases in the X basis on each qubit. Default is zeros(n) constant*field_z - vector of constant biases in the Z basis on each qubit. Default is zeros(n)
