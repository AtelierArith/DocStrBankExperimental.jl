```
bad_primes(L::HermLat; discriminant::Bool = false, dyadic::Bool = false)
                                                         -> Vector{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}}
```

Given a hermitian lattice `L` over $E/K$, return the prime ideals of $\mathcal O_K$ dividing the scale or the volume of `L`.

If `discriminant == true`, the prime ideals dividing the discriminant of $\mathcal O_E$ are returned. If `dyadic == true`, the prime ideals dividing $2*\mathcal O_K$ are returned.
