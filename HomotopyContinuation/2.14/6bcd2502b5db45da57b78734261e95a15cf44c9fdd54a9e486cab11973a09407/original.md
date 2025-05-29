```
certify(F, solutions, [p, certify_cache]; options...)
certify(F, result, [p, certify_cache]; options...)
```

Attempt to certify that the given approximate `solutions` correspond to true solutions of the polynomial system $F(x;p)$. The system $F$ has to be an (affine) square polynomial system. Also attemps to certify for each solutions whether it approximates a real solution. The certification is done using interval arithmetic and the Krawczyk method[^Moo77]. Returns a [`CertificationResult`](@ref) which additionall returns the number of distinct solutions. For more details of the implementation see [^BRT20].

## Options

  * `show_progress = true`: If `true` shows a progress bar of the certification process.
  * `max_precision = 256`: The maximal accuracy (in bits) that is used in the certification process.
  * `compile = false`: See the [`solve`](@ref) documentation.

## Example

We take the [first example](https://www.juliahomotopycontinuation.org/guides/introduction/#a-first-example) from our introduction guide.

```julia
@var x y
# define the polynomials
f₁ = (x^4 + y^4 - 1) * (x^2 + y^2 - 2) + x^5 * y
f₂ = x^2+2x*y^2 - 2y^2 - 1/2
F = System([f₁, f₂], variables = [x,y])
result = solve(F)
```

```
Result with 18 solutions
========================
• 18 paths tracked
• 18 non-singular solutions (4 real)
• random seed: 0xcaa483cd
• start_system: :polyhedral
```

We see that we obtain 18 solutions and it seems that 4 solutions are real. However, this is based on heuristics. To be absolute certain we can certify the result

```julia
certify(F, result)
```

```
CertificationResult
===================
• 18 solution candidates given
• 18 certified solution intervals (4 real, 14 complex)
• 18 distinct certified solution intervals (4 real, 14 complex)
```

and see that there are indeed 18 solutions and that they are all distinct.

[^Moo77]: Moore, Ramon E. "A test for existence of solutions to nonlinear systems." SIAM Journal on Numerical Analysis 14.4 (1977): 611-615.

[^BRT20]: Breiding, P., Rose, K. and Timme, S. "Certifying zeros of polynomial systems using interval arithmetic." arXiv:2011.05000.
