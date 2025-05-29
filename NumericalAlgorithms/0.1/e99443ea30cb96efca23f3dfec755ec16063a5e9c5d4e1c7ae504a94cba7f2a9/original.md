```
FindRoot1D(f::Function, p0::Float64, p1::Float64, NMAX::UInt64, tol::Float64)
```

Compute one-dimensional root of a function with secant method. Secant method is defined by the difference equation:

$$
x_{n}=x_{n-1}-f(x_{n-1}){\frac {x_{n-1}-x_{n-2)){f(x_{n-1})-f(x_{n-2})))={\frac {x_{n-2}f(x_{n-1})-x_{n-1}f(x_{n-2})}{f(x_{n-1})-f(x_{n-2})))
$$
