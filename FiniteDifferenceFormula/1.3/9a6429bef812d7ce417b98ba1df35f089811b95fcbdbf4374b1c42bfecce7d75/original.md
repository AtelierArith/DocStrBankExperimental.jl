`verifyformula`(n, points, k, m = 1) or `activatejuliafunction`(n, points, k, m = 1)

Verify if a formula is valid. If it is valid, generate and activate its Julia function(s). If not, try to find a formula for the derivative using the points.

```
     n: the n-th order derivative
points: in the format of a range, start : stop, or a vector
     k: a list of the coefficients in a formula
     m: the coefficient in the denominator of a formula
```

# Examples

```julia-repl
import FiniteDifferenceFormula as fd
fd.verifyformula(1,[-1,2],[-3,4],5)  # f'(x[i]) = (-3f(x[i-1])+4f(x[i+2]))/(5h)?
fd.verifyformula(2, -3:3, [2,-27,270,-490,270,-27,2], 18)
fd.activatejuliafunction(2, -3:3, [1/90,-3/20,3/2,-49/18,3/2,-3/20,1/90])
fd.verifyformula(2, -3:3, [1//90,-3//20,3//2,-49//18,3//2,-3//20,1//90])
```
