```
compress!(X::LDLᵀ)
```

Concatenate the internal components and perform a column compression following [^Lang2015].

This is an expensive operation.

See also: [`concatenate!`](@ref), [`orthf`](@ref)

[^Lang2015]: N Lang, H Mena, and J Saak, "On the benefits of the LDLT factorization for large-scale differential matrix equation solvers" Linear Algebra and its Applications 480 (2015): 44-71. [doi:10.1016/j.laa.2015.04.006](https://doi.org/10.1016/j.laa.2015.04.006)
