```
anneal(linear::AbstractDict, quad::AbstractDict; [, opts])
```

Solve forward ising problem expressed by `linear` and `quad` biases.

# Arguments

  * `linear::Dict`: Linear biases meaning that magnetic field.
  * `quad::Dict`: Quadratic biases meaning that spin-spin interaction.

Options that can be provided in the `opts` dictionary:

  * `:beta_min` - Initial (minimal) value of inverse temperature. (default: 5.0)
  * `:beta_max` - Final (maximal) value of inverse temperature. (default: 15.0)
  * `:n_sweep` - Number of division between `beta_min` and `beta_max`. (default: 1000)
  * `:n_read` - Number of run repetitions of Simulated Annealing. (default: 1)

# Examples

```jldoctest
julia> using InverseIsing

julia> h = Dict(:a => 1) # Setting field biases.

julia> J = Dict((:a, :b) => -1) # Setting interaction.

julia> response = anneal(h, J)

julia> response.sample
Dict{Symbol,Int64} with 2 entries:
  :a => 1
  :b => -1
```
