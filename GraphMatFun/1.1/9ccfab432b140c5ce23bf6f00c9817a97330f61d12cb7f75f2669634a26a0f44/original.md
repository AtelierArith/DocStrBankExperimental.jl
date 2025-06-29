```
opt_linear_fit!(
    graph,
    objfun,
    discr,
    linear_cref;
    input = :A,
    errtype = :abserr,
    linlsqr = :backslash,
    droptol = 0,
)
```

Linear fitting of a `graph` of the form

```
c_1 g_1(x) + c_2 g_2(x) + … + c_n g_n(x)
```

to the values of `objfun`, in the points `discr`. Reference to the coefficients `c_1,…,c_n` should be given `linear_cref`.

The variable `graph` is modified during the iterations and the function has no return value.

See [`opt_gauss_newton!`](@ref) for a description the kwarg `errtype` and `input`, and [`solve_linlsqr!`](@ref) for the kwargs `linlsqr and`droptol`.
