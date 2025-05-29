```
hermitian_genera(E::NumField, rank::Int,
                              signatures::Dict{InfPlc, Int},
                              determinant::Union{Hecke.RelNumFieldOrderIdeal, Hecke.RelNumFieldOrderFractionalIdeal};
                              min_scale::Union{Hecke.RelNumFieldOrderIdeal, Hecke.RelNumFieldOrderFractionalIdeal} = is_integral(determinant) ? inv(1*order(determinant)) : determinant,
                              max_scale::Union{Hecke.RelNumFieldOrderIdeal, Hecke.RelNumFieldOrderFractionalIdeal} = is_integral(determinant) ? determinant : inv(1*order(determinant)))
                                                                                                             -> Vector{HermGenus}
```

Return all global genus symbols for hermitian lattices over the algebra`E` with rank `rank`, signatures given by `signatures`, scale bounded by `max_scale` and determinant class equal to `determinant`.

If `max_scale == nothing`, it is set to be equal to `determinant`.
