```
bernoulli(n, x)
```

Calculates Bernoulli polynomials $B_n(x)$  e.g., see

  * [https://en.wikipedia.org/wiki/Bernoulli_polynomials](https://en.wikipedia.org/wiki/Bernoulli_polynomials)
  * [http://dlmf.nist.gov/24](http://dlmf.nist.gov/24)

## Arguments

  * $n$ `::Integer`: the index into the series, $n=0,1,2,3,...$
  * $x$ `::Real`: the point at which to calculate the polynomial

## Examples

```jldoctest; setup = :(using Polylogarithms)
julia> bernoulli(6, 1.2)
0.008833523809524735
```
