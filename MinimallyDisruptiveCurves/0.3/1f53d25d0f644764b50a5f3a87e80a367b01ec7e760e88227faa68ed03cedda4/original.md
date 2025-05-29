```
HamiltonianResidual(timepoints::AbstractRange)
HamiltonianResidual(timepoints::Vector{<:AbstractFloat})
```

Print @info REPL output on the numerical value of dHdu, the u-derivative of the Hamiltonian, at timepoints::Vector{<:AbstractFloat}

Example c = HamiltonianResidual(0.1:0.1:2.1)

c can then be used as an argument to Verbose(), which then goes as a keyword argument into evolve.
