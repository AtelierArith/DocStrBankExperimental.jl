```
evolve_operator(evo_gen, time)
```

Return an exponent of `time`×`evo_gen`. This function is useful in the case of multiple initial states and fixed `evo_gen` and `time`, as it is faster to compute the exponent once and use it for evolving on different initial states.

*Note:* Parameter `evo_gen` must be of type `Matrix`. For type `SparseMatrixCSC` case different numerical approach is used. See function `epmv` in package `Expokit`.

# Examples

```jldoctest; setup = :(using QSWalk)
julia> H, L = [0 1; 1 0], [[0 1; 0 0], [0 0; 1 0]]
([0 1; 1 0], Array{Int64,2}[[0 1; 0 0], [0 0; 1 0]])

julia> evolve_operator(evolve_generator(H, L), 4.0)
4×4 Array{Complex{Float64},2}:
 0.499815+0.0im                0.0+0.00127256im  …  0.500185+0.0im
      0.0+0.00127256im  0.00960957+0.0im                 0.0-0.00127256im
      0.0-0.00127256im  0.00870607+0.0im                 0.0+0.00127256im
 0.500185+0.0im                0.0-0.00127256im     0.499815+0.0im
```
