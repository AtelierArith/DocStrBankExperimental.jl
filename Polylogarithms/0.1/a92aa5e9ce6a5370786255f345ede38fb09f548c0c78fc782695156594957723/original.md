```
bernoulli(n)
```

Calculates the first 35 Bernoulli numbers $B_n$  (of the first-kind or NIST type)   e.g., see

  * [http://mathworld.wolfram.com/BernoulliNumber.html](http://mathworld.wolfram.com/BernoulliNumber.html)
  * [https://en.wikipedia.org/wiki/Bernoulli_number](https://en.wikipedia.org/wiki/Bernoulli_number)
  * [http://dlmf.nist.gov/24](http://dlmf.nist.gov/24)

N.B. Bernoulli numbers of second kind only seem to differ in that $B_1 = + 1/2$ (instead of -1/2)

## Arguments

  * $n$ `::Integer`: the index into the series, $n=0,1,2,3,...,35$ (for larger $n$ use `bernoulli(n,0.0)` )

We only provide the 1st 36 values as beyond this, we can't  return Int64 rationals, so best to compute the real approximation  using `bernoulli(n,0.0)`. 

Odd values for $n>1$ are all zero.

## Examples

```jldoctest; setup = :(using Polylogarithms)
julia> bernoulli(6)
1//42
```
