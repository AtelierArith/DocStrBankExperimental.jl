s段のガウス台帳

```julia
TableauGauss(::Type{T}, s)
TableauGauss(s) = TableauGauss(Float64, s)
```

コンストラクタは、段数`s`とオプションで台帳の要素型`T`を受け取ります。

参考文献:

```
John C. Butcher.
Implicit Runge-Kutta processes.
Mathematics of Computation, Volume 18, Pages 50-64, 1964.
doi: 10.1090/S0025-5718-1964-0159424-9.

John C. Butcher.
Gauss Methods. 
In: Engquist B. (eds). Encyclopedia of Applied and Computational Mathematics. Springer, Berlin, Heidelberg. 2015.
doi: 10.1007/978-3-540-70529-1_115.
```
