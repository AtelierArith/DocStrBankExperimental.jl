```
q_translate_state(h::String; normal=false)
```

Convert a string representation of quantum state to a vector. The keyword argument `normal` indicates whether to normalize the output vector. (Currently only '0' and '1' are supported)

# Examples

Single term:

```julia-repl
julia> q_translate_state("001")
8-element Array{Complex{Float64},1}:
 0.0 + 0.0im
 1.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
```

Multiple terms:

```julia-repl
julia> q_translate_state("(101)+(001)", normal=true)
8-element Array{Complex{Float64},1}:
                0.0 + 0.0im
 0.7071067811865475 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
 0.7071067811865475 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
```
