Main function for performing quantum annealing simulation via a Magnus Expansion (second order). Noise can be simulated by running multiple times with randomized constant fields.

Arguments: ising*model - ising model represented as a dictionary.  The qubits               and couplings are represented as tuples, and the weights               are numbers.               For Example: im = Dict((1,) => 1, (2,) => 0.5, (1,2) => 2) annealing*schedule - The annealing schedule, of the form given by the struct

Parameters: initial*state - Initial state vector. Defaults to uniform superposition state on n qubits constant*field*x - vector of constant biases in the X basis on each qubit. Default is zeros(n) constant*field*z - vector of constant biases in the Z basis on each qubit. Default is zeros(n) The parameters `mean*tol`and`max_tol`specify the desired simulation accuracy. The`silence` parameter can be used to suppress the progress log.
