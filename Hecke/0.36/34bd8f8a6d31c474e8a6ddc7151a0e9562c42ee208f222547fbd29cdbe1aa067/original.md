```
integral_closure(R, F)
```

Computes the integral closure of the ring $R$ in the field $F$. $F$ needs to be a finite extension over the fraction field of $R$. The algorithm uses a variant of the Round-2 method.

Currently supported are

  * $$
    R
    $$

    the integers and $F$ an (absolute simple) number field. Here the result is an number field order.
  * $$
    R
    $$

    a localisation of the integers and $F$ an (absolute simple) number. Here the result is a generic order.
  * $$
    R
    $$

    a univariate polynomial ring over a field $k$ and $F$ a function field (finite extension of $k(t)$.
  * $$
    R
    $$

    the degree-localisation of a univariate polynomial ring over a field $k$ amd $F$ a finite extension of $k(t)$
  * $$
    R
    $$

    a univariate polynomial ring over the integers and $F$ a finite extension of $Q(t)$ for the rational field $Q$.

# EXAMPLES

```julia
julia> k, a = quadratic_field(12);

julia> integral_closure(ZZ, k)

Maximal order of real quadratic field defined by x^2 - 12
with basis AbsSimpleNumFieldElem[1, 1//2*sqrt(12)]
```
