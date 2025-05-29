```
computational_basis_vectors( dim::Int64 ) ::Vector{ Vector{Int64} }
```

Returns the set of orthonormal column vectors $\{|1\rangle,\dots,|i\rangle,\dots,|d\rangle \}$ spanning a vector space of dimension `dim`. Note that $|1\rangle = ( 1, 0, \dots, 0 )^T$.
