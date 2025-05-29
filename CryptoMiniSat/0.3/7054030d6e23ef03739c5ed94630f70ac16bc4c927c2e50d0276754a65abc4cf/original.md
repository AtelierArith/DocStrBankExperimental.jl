`solve(clauses; verbose::Integer=0, num_threads::Int = Sys.CPU_THREADS)`

  * `verbose` - verbosity
  * `num_threads` - number of CPU threads to use

Returns a solution if the problem is satisfiable. Satisfiable solutions are represented as a dictionary.

The first argument is a vector of clauses. Each clause is a vector of literals of, each encapsulated in `Lit(T)`, `NotLit(T)`, `XorLit(T)` or `XNorLit(T)` for some type `T`. Each clause containing XorLit and XNotLit terms is an XOR clause, and the number of satisfied clauses must have the same parity as the number of NotLit and XNorLit for the clause to be satified. Clauses containing Lit and NotLit terms are usual disjunctive clauses.

If the problem is not satisfiable the method returns an `:unsatisfiable` symbol.

```julia
julia> import CryptoMiniSat
julia> # coffee with cream, tea with milk
julia> cnf = [[XorLit(:coffee),XorLit(:tea)],[NotLit(:coffee),Lit(:cream)],[NotLit(:tea),Lit(:milk)]];
julia> CryptoMiniSat.solve(cnf)
Dict{Symbol, Bool} with 3 entries:
  :cream  => 0
  :milk   => 1
  :tea    => 1
  :coffee => 0
```
