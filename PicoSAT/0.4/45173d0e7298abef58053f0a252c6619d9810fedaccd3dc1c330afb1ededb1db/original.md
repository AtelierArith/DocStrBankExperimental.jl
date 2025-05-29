`solve(clauses; vars::Integer=-1, verbose::Integer=0, proplimit::Integer=0)`

  * `vars` - the number of variables
  * `verbose` - prints solver logs to `STDOUT` when `verbose > 0` with increasing detail.
  * `proplimit` - helps to bound the execution time.  The number of propagations and the solution time are roughly linearly related.  A value of 0 (default) allows for an unbounded number of propagations.

Returns a solution if the problem is satisfiable. Satisfiable solutions are represented as a vector of signed integers. If the problem is not satisfiable the method returns an `:unsatisfiable` symbol. If a solution cannot be found within the defined propagation limit, an `:unknown` symbol is returned.

```julia
julia> import PicoSAT
julia> cnf = Any[[1, -5, 4], [-1, 5, 3, 4], [-3, -4]];
julia> PicoSAT.solve(cnf)
5-element Array{Int64,1}:
   1
  -2
  -3
  -4
   5
```
