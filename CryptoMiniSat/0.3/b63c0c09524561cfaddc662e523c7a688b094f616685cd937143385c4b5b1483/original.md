`itersolve(clauses; vars::Integer=-1, verbose::Integer=0, proplimit::Integer=0, num_threads::Integer=Sys.CPU_THREADS)`

  * `vars` - the number of variables
  * `verbose` - verbosity
  * `proplimit` - ignored
  * `num_threads` - number of CPU threads to use

Returns an iterable object over all solutions.

```julia
julia> import CryptoMiniSat
julia> cnf = [[1, -5, 4], [-1, 5, 3, 4], [-3, -4]];
julia> collect(CryptoMiniSat.itersolve(cnf))
18-element Array{Any,1}:
 [-1, -2, -3, -4, -5]
 [-1, 2, -3, -4, -5]
 [-1, 2, 3, -4, -5]
 [1, 2, 3, -4, 5]
 [-1, -2, -3, 4, -5]
 [1, -2, 3, -4, 5]
 [-1, -2, -3, 4, 5]
 [-1, 2, -3, 4, -5]
 [1, -2, -3, 4, 5]
 [1, 2, -3, 4, 5]
 [1, 2, -3, 4, -5]
 [-1, 2, -3, 4, 5]
 [1, -2, -3, 4, -5]
 [1, -2, 3, -4, -5]
 [-1, -2, 3, -4, -5]
 [1, 2, -3, -4, 5]
 [1, -2, -3, -4, 5]
 [1, 2, 3, -4, -5]
```
