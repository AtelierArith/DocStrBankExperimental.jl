`decimalplaces`() or `decimalplaces`(n)

Show present decimal places for generating Julia function(s) of computed formulas, if no argument is passed to `decimalplaces`. Otherwise, set the decimal places to n.

# Examples

```
import FiniteDifferenceFormula as fd
fd.compute(2,-3:3)
fd.formula()  # by default, use 16 decimal places to generate a Julia function
fd.decimalplaces(4)
fd.formula()  # now, use 4 decimal places to generate a Julia function
```
