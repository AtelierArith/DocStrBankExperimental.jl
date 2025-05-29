```
stieltjes(n)
```

Provides the first 10 Stieltjes (generalized Euler-Mascheroni) constants (see  Abramowitz and Stegunm, 23.2.5) or [https://en.wikipedia.org/wiki/Stieltjes_constants](https://en.wikipedia.org/wiki/Stieltjes_constants).

There is a table at "The Generalized Euler-Mascheroni Constants", O.R. Ainsworth and L.W.Howell  NASA Technical Paper 2264, Jan 1984  [https://ntrs.nasa.gov/archive/nasa/casi.ntrs.nasa.gov/19840007812.pdf](https://ntrs.nasa.gov/archive/nasa/casi.ntrs.nasa.gov/19840007812.pdf)  but the OEIS has more accurate values, which will be useful when I get around to   bit float versions of the code.

Note that stieltjes(0) = γ, the Euler–Mascheroni constant, also called just Euler's constant.   [https://en.wikipedia.org/wiki/Euler-Mascheroni_constant](https://en.wikipedia.org/wiki/Euler%E2%80%93Mascheroni_constant)

## Arguments

  * `n::Integer`: the number of elements to compute.

## Examples

```jldoctest; setup = :(using Polylogarithms)
julia> stieltjes(0)
0.5772156649015329
```
