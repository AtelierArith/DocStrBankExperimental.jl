```
IMEXEulerARK(;kwargs...)
```

The one-step version of the IMEX multistep methods of

  * Uri M. Ascher, Steven J. Ruuth, Brian T. R. Wetton. Implicit-Explicit Methods for Time-Dependent Partial Differential Equations. Society for Industrial and Applied Mathematics. Journal on Numerical Analysis, 32(3), pp 797-823, 1995. doi: [https://doi.org/10.1137/0732037](https://doi.org/10.1137/0732037)

When applied to a `SplitODEProblem` of the form

```
u'(t) = f1(u) + f2(u)
```

A classical additive Runge-Kutta method in the sense of [Araújo, Murua, Sanz-Serna (1997)](https://doi.org/10.1137/S0036142995292128) consisting of the implicit and the explicit Euler method given by

```
y1   = uold + dt * f1(y1)
unew = uold + dt * (f1(unew) + f2(y1))
```

See also `SBDF`, `IMEXEuler`.
