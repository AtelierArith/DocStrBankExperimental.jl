```
complex_powers(z, m)
```

Compute integer powers of `z` from `z^0` through `z^m`, recursively.

Note that `z` is assumed to be normalized, with complex amplitude approximately 1.

This algorithm is mostly due to Stoer and Bulirsch in "Introduction to Numerical Analysis" (page 24) — with a little help from de Moivre's formula, which is essentially exp(iθ)ⁿ = exp(inθ), as well as my own alterations to deal with different behaviors in different quadrants.

There isn't usually a huge advantage to using this specialized function.  If you just need a particular power, it will generally be far more efficient and just as accurate to compute either exp(iθ)ⁿ or exp(inθ) explicitly.  However, if you need all powers from 0 to m, this function is about 10 or 5 times faster than those options, respectively, for large m.  Like those options, this function is numerically stable, in the sense that its errors are usually smaller than `m` times the error from machine-precision errors in the input argument — or at worst about 50% larger, which occurs as the phase approaches multiples of π/2.

See also: [`complex_powers!`](@ref)
