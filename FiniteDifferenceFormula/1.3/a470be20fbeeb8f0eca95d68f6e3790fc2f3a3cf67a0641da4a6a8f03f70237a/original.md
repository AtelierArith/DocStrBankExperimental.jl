`findbackward`(n, points, printformulaq = false)

Compute a formula for the nth order derivative using the given points.

For the input, `n` and `points` (See [`compute`]), there may not be formulas which use the two end points like -2 and 3 in -2 : 3 or [-2, -1, 0, 1, 2, 3]. In this case, `findbackward` tries to find a formula by shrinking the range from the right endpoint to, first -2 : 2, then, -2 : 1, then -2 : 0, and so on, until a formula is found or no formulas can be found at all.

See also [`compute`], [`find`], and [`findforward`].

# Examples

```
import FiniteDifferenceFormula as fd
fd.compute(3,-100:50)
# output: ***** Warning: 3, -100:22 might be your input for which a formula is found.
fd.findbackward(3,-99:50)
# output: (3, -99:23, ...)
```
