`itersolve(clauses; vars::Integer=-1, verbose::Integer=0, proplimit::Integer=0)`

  * `vars` - the number of variables
  * `verbose` - prints solver logs to `STDOUT` when `verbose > 0` with increasing detail.
  * `proplimit` - helps to bound the execution time.  The number of propagations and the solution time are roughly linearly related.  A value of 0 (default) allows for an unbounded number of propagations.

Returns an iterable object over all solutions. When a user-defined propagation limit is specified, the iterator may not produce all feasible solutions.

```julia
julia> import PicoSAT
julia> cnf = Any[[1, -5, 4], [-1, 5, 3, 4], [-3, -4]];
julia> PicoSAT.itersolve(cnf)
julia> for sol in PicoSAT.itersolve(cnf)
           println(sol)
       end
[1,-2,-3,-4,5]
[1,-2,-3,4,-5]
[1,-2,-3,4,5]
[1,-2,3,-4,-5]
...
```
