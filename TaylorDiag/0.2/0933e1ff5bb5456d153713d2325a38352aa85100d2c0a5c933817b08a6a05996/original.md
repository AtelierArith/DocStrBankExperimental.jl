```
COR(Cr::AbstractArray,C::AbstractArray)
```

Compute the correlation coefficient between reference collection Cr and C. Note: the function exactly returns the minimum between 1.0 and the formula because of numerical errors.

```julia
Cr = [1.0, 2.0, 3.0]
C  = [1.0, 2.0, 3.0]
Correlation = sum( (C.-mean(C)) .* (Cr.-mean(Cr)) ) ./ (length(C) .* STD(C) .* STD(Cr))
```

In this case, `correlation=1.0000000000000002`, or `correlation=1+2e-16`, being the computational error because of (1/3) (and multiples) rounding.
