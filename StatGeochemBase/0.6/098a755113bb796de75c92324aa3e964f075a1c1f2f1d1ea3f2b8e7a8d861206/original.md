```julia
draw_from_distribution(dist::Collection{AbstractFloat}, n::Integer)
```

Draw `n` random floating point numbers from a continuous probability distribution specified by a collection `dist` defining the PDF curve thereof.

### Examples

```julia
julia> draw_from_distribution([0,1,2,1,0.], 7)
7-element Vector{Float64}:
 0.5271744125470383
 0.6624591724796276
 0.7737643383545575
 0.9603780726501608
 0.7772477857811155
 0.8307248435614027
 0.6351766227803024    
```
