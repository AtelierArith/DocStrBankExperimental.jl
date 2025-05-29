`findforward`(n, points, printformulaq = false)

Compute a formula for the nth order derivative using the given points.

For the input, `n` and `points` (See [`compute`]), there may not be formulas which use the two end points like -2 and 3 in -2 : 3 or [-2, -1, 0, 1, 2, 3]. In this case, `findforward` tries to find a formula by shrinking the range from the left endpoint to, first -1 : 3, then, 0 : 3, then 1 : 3, and so on, until a formula is found or no formulas can be found at all.

See also [`compute`], [`find`], and [`findbackward`].

# Examples

```
import FiniteDifferenceFormula as fd
fd.findforward(2, -10:9)
```
