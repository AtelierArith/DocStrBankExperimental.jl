```
genus(HermLat, E::NumField, p::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, data::Vector; type::Symbol = :det,
	                                           check::Bool = true)
                                                             -> HermLocalGenus
```

Construct the local genus symbol `g` for hermitian lattices over the algebra `E`, with base field $K$, at the prime ideal `p` of $\mathcal O_K$. Its invariants are specified by `data`.

  * If the prime ideal is good (not ramified-and-dyadic), the elements of `data` must be `(s, r, d)::Tuple{Int, Int, Int}` where `s` refers to the scale $\mathfrak P$-valuation, `r` the rank and `d` the determinant/discriminant class of a Jordan block of `g`, where $\mathfrak P$ is a prime ideal of $\mathcal O_E$ lying over `p`.

    In the unramified case, `d` is determined by `s` and `r` and can be omitted. Hence also `(s, r)::Tuple{Int, Int}` is allowed.
  * If the prime ideal is bad (ramified and dyadic), the elements of `data` must be `(s, r, d, n)::Tuple{Int, Int, Int, Int}`, where in addition `n` refers to the norm `p`-valuation.

Additional comments:

  * `d` must be in $\{[1, -1\}$;
  * If `type == :disc`, the parameter `d` is interpreted as the discriminant;
  * Sanity checks can be disabled by setting `check == false`.
