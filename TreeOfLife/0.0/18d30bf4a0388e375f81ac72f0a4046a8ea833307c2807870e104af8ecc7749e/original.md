```
getconsensus(trees::Vector{<:AbstractTree}; 
	threshold::Float64=0.5, every::Int=0) :: CladoTree
```

Summarize phylogenetic trees to one such that clades with support rate no less  than a threshold remain in the consensus tree. 

The argument `threshold` should be a number between `0.5` and `1.0`; the default  value is `0.5`.

The argument `every`, if set to a positive integer, makes the (probably long)  analyzing process print a log per `every` trees; the default value is `0`.
