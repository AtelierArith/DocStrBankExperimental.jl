`taylor`()

  * Print the first few nonzero terms of the Taylor series of the linear combination k[0]f(x[i+j0]) + k[1]f(x[i+j1]) + ... for the newly computed formula (even if failed).

`taylor`(j, n = 10)

  * Print the 1st n terms of Taylor series of f(x[i+j]) about x[i].

`taylor`(coefs, n = 10), or

  * Print the 1st n terms of Taylor series with coefficients in 'coefs'

`taylor`(points, k, n::Int = 10)

  * Prints the 1st n nonzero terms of the Taylor series of the linear combination:  k[0]f(x[i+points[0]]) + k[1]f(x[i+points[1]]) + ...

The last two provide also another way to verify if a formula is mathematically valid or not.

See also [`verifyformula`], [`activatejuliafunction`], and [`taylorcoefs`].

# Examples

```
import FiniteDifferenceFormula as fd
fd.compute(1, [0, 1, 5, 8])
fd.taylor()

fd.taylor(2)

n = 50
coefs = 2*fd.tcoefs(0, n) - 6*fd.tcoefs(1, n) + 4*fd.tcoefs(2, n)
fd.taylor(coefs, n) # this n can be any positive integer

fd.taylor(-fd.tcoefs(0) + 3*fd.tcoefs(1) - 3*fd.tcoefs(2) + fd.tcoefs(3))
fd.taylor(0:3, [-1, 3, -3, 1], 6)
```
