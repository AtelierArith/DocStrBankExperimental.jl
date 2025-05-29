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

`objfun`の値に対して、`discr`の点での形の`graph`の線形フィッティング

```
c_1 g_1(x) + c_2 g_2(x) + … + c_n g_n(x)
```

は、係数`c_1,…,c_n`に対して`linear_cref`を指定する必要があります。

変数`graph`は反復中に変更され、関数は戻り値を持ちません。

`errtype`および`input`のkwargの説明については[`opt_gauss_newton!`](@ref)を、`linlsqr`および`droptol`のkwargsについては[`solve_linlsqr!`](@ref)を参照してください。
