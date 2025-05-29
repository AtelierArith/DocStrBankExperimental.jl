```
harmonic(n::Integer,r::Integer)
```

Calculates generalized harmonic numbers    e.g., see [http://mathworld.wolfram.com/HarmonicNumber.html](http://mathworld.wolfram.com/HarmonicNumber.html)  using a better approach which works when both inputs are integers  [https://carma.newcastle.edu.au/resources/jon/Preprints/Papers/Published-InPress/Oscillatory%20(Tapas%20II)/Papers/coffey-zeta.pdf](https://carma.newcastle.edu.au/resources/jon/Preprints/Papers/Published-InPress/Oscillatory%20(Tapas%20II)/Papers/coffey-zeta.pdf), p.341

## Arguments

  * $n$ `::Integer`: non-negative index 1 of the Harmonic number to calculate
  * $r$ `::Integer`: index 2 of the Harmonic number to calculate

## Examples

```jldoctest; setup = :(using Polylogarithms)
julia> harmonic(2,1)
1.5000000000000002
```
