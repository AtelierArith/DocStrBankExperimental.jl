`solve(clauses; vars::Integer=-1, verbose::Integer=0, proplimit::Integer=0, num_threads::Int = Sys.CPU_THREADS)`

  * `vars` - the number of variables (will be inferred if not specified)
  * `verbose` - verbosity
  * `proplimit` - ignored
  * `num_threads` - number of CPU threads to use

Returns a solution if the problem is satisfiable. Satisfiable solutions are represented as a vector of signed integers. If the problem is not satisfiable the method returns an `:unsatisfiable` symbol.

```julia
julia> import CryptoMiniSat
julia> cnf = [[1, -5, 4], [-1, 5, 3, 4], [-3, -4]];
julia> CryptoMiniSat.solve(cnf)
5-element Array{Int64,1}:
 -1
 -2
 -3
 -4
 -5
```
