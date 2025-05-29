```
PhaseRelativePermeability(s, k; label = :w, connate = s[1], epsilon = 1e-16)
```

Type that stores a sorted phase relative permeability table (given as vectors of equal length `s` and `k`):

$K_r = K(S)$

Optionally, a label for the phase, the connate saturation and a small epsilon value used to avoid extrapolation can be specified. The return type holds both the table, the phase context, the autodetected critical and maximum relative permeability values and can be passed saturation values to evaluate the underlying function:

```jldoctest
s = range(0, 1, 50)
k = s.^2
kr = PhaseRelativePermeability(s, k)
round(kr(0.5), digits = 2)

# output

0.25
```
