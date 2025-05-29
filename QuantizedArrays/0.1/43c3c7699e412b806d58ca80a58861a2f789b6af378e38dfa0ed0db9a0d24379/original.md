```
CodeBook{U<:Unsigned,T}
```

The codebook structure. It holds the codes corresponding to the vector prototypes and the mapping bethween the codes and prototypes.

# Fields

  * `codes::Vector{U}` the codes
  * `vectors::Matrix{T}` the prototypes
  * `codemap::Dict{U,Int}` mapping from code to column in `vectors`
