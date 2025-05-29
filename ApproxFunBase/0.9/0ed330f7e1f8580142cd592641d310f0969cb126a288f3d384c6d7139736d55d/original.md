```
\(A::Operator,b;tolerance=tol,maxlength=n)
```

solves a linear equation, usually differential equation, where `A` is an operator or array of operators and `b` is a `Fun` or array of funs.  The result `u` will approximately satisfy `A*u = b`.
