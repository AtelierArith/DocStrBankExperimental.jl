`representation(W,i)`

returns,   for  the  `i`-th  irreducible   representation  of  the  complex reflection  group or Spets `W`, a list of matrices images of the generating reflections  of `W` in a model of the representation (for Spets, the result is  a `NamedTuple` with fields `gens`,  a representation of `Group(W)`, and `F`,  the matrix for `W.phi` in the representation). This function is based on  the  classification,  and  is  not  yet fully implemented for `G₃₄`; 78 representations  are  missing  out  of  169,  that  is,  representations of dimension ≥140, except half of those of dimensions 315, 420 and 840.

```julia-repl
julia> representation(complex_reflection_group(24),3)
3-element Vector{Matrix{Cyc{Int64}}}:
 [1 0 0; -1 -1 0; -1 0 -1]
 [-1 0 -1; 0 -1 (1-√-7)/2; 0 0 1]
 [-1 -1 0; 0 1 0; 0 (1+√-7)/2 -1]
```
