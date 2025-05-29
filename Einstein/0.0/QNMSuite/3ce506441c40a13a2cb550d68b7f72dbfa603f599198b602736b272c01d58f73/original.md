```
continued_fraction_lentz([TF=Float64], a::Function, b::Function, tol::TF, min_iter::Integer, max_iter::Integer) where {TF<:AbstractFloat}
```

Compute the continued fraction

$$
f(x)=b_0+\frac{a_1}{b_1+\frac{a_2}{b_2+\frac{a_3}{b_3+\frac{a_4}{b_4+\frac{a_5}{b_5+\cdots}}}}}
$$

using modified Lentz's method. Translated from [duetosymmetry/qnm](https://github.com/duetosymmetry/qnm).

# Arguments

  * `a`: A function that returns the `aᵢ` terms.
  * `b`: A function that returns the `bᵢ` terms.
  * `tol`: The tolerance for convergence.
  * `min_iter`: The minimum number of iterations to perform.
  * `max_iter`: The maximum number of iterations to perform.

# Returns

  * `fᵢ`: The value of the continued fraction.
  * `errorᵢ`: The estimated error.
  * `i`: The number of iterations performed.

# Examples

## Compute the square root of two using continued fractions

$$
\sqrt{2} = 1 + \frac{1}{2 + \frac{1}{2 + \frac{1}{2 + \frac{1}{2 + \cdots}}}} \approx 1.414213562373095
$$

```julia
a(i) = 1
b(i) = i == 0 ? 1 : 2
continued_fraction_lentz(Float64, a, b, 10*eps(Float64), 50, 1000)
```

## Compute Golden Ratio

$$
\phi = 1 + \frac{1}{1 + \frac{1}{1 + \frac{1}{1 + \cdots}}} \approx 1.618033988749895
$$

```julia
a(i) = 1
b(i) = 1
continued_fraction_lentz(Float64, a, b, 10*eps(Float64), 50, 1000)
```

# References

  * [qnm/qnm/contfrac.py at master · duetosymmetry/qnm](https://github.com/duetosymmetry/qnm/blob/master/qnm/contfrac.py)
  * [press2007numerical, Stein:2019mop, lentz1976generating, thompson1986coulomb, DLMF*3103*online](@cite)
