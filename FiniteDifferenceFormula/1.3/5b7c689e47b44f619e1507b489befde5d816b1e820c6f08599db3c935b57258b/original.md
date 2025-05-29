`taylorcoefs`(j, n = 10))

Compute and return coefficients of the first n terms of the Taylor series of f(x[i + j]) = f(x[i] + jh) about x[i], where h is the increment in x.

# Examples

```
import FiniteDifferenceFormula as fd
fd.taylorcoefs(-2)
fd.taylorcoefs(5, 4)
```
