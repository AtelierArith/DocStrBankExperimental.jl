```julia
makeSolverData!(dfg; solvable, varList, solveKey)

```

For variables in `varList` check and if necessary make solverData objects for both `:default` and `:parametric` solveKeys. 

Example

```julia
num_made = makeSolverData(fg; solveKey=:parametric)
```

Notes

  * Part of solving JuliaRobotics/IncrementalInference.jl issue 1637

DevNotes

  * TODO, assumes parametric solves will always just be in solveKey `:parametric`.

See also: [`doautoinit!`](@ref), [`initAll!`](@ref)
