```
polylog(s, z, Diagnostics())
```

Calculates the Polylogarithm function ${Li}_s(z)$ defined by

${Li}_s = \sum_{n=1}^{\infty} \frac{z^n}{n^s}$

Uses double precision complex numbers (not arbitrary precision). It's goal is an relative error bound 10^{-12}.

## Input Arguments

  * $s::$ `Complex`: the 'fractional' parameter
  * $z$ `::Complex`: the point at which to calculate it
  * `::Diagnostics`: use this to indicate that the output should include extra information

It should also accept input arguments as `Real` or `Rational` or `Integer` but these aren't completely tested.

There are additional keywords, but these are currently intended for testing not use.

## Output Arguments

  * $Li_s(z)$: The result
  * $n$:       The number of elements used in each series
  * `series`:    The series used to compute results (4 = reciprocal)

## Examples

```jldoctest; setup = :(using Polylogarithms)
julia> polylog(0.35, 0.2, Diagnostics() )
(0.23803890574407033, 17, 1)
```
