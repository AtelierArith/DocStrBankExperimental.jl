```
harmonic(n::Integer)
```

Calculates harmonic numbers,    e.g., see [http://mathworld.wolfram.com/HarmonicNumber.html](http://mathworld.wolfram.com/HarmonicNumber.html)

## Arguments

  * $n$ `::Integer`: non-negative index of the Harmonic number to calculate

## Examples

```jldoctest; setup = :(using Polylogarithms)
julia> harmonic(2)
1.5
```
