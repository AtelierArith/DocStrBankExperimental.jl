```
harmonic(n::Integer,r::Real)
```

Calculates generalized harmonic numbers,     e.g., see [http://mathworld.wolfram.com/HarmonicNumber.html](http://mathworld.wolfram.com/HarmonicNumber.html)

## Arguments

  * $n$ `::Integer`: non-negative index 1 of the Harmonic number to calculate
  * $r$ `::Real`: index 2 of the Harmonic number to calculate

It should be possible to extend this to complex r, but that requires more testing.

## Examples

```jldoctest; setup = :(using Polylogarithms)
julia> harmonic(2,1.5)
1.3535533905932737
```
