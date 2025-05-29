```
itp = interpolate(A, interpmode, gridstyle, λ, k)
```

配列 `A` を、`interpmode` と `gridstyle` によって決定されるモードで補間し、[1] に従った正則化を行い、次数 `k` と定数 `λ` を使用します。 `interpmode` は次のいずれかである可能性があります。

  * `BSpline(NoInterp())`
  * `BSpline(Linear())`
  * `BSpline(Quadratic(BC()))` （[`BoundaryCondition`](@ref）を参照）
  * `BSpline(Cubic(BC()))`

異なる補間スキームを各軸に沿って使用したい場合は、そのような値のタプルであることもできます。

`gridstyle` は `OnGrid()` または `OnCell()` のいずれかである必要があります。

`k` はペナルティをかける導関数に対応します。 λ->∞ の極限では、補間関数は次数 `k-1` の多項式になります。値 2 が最も一般的です。

`λ` は非負です。値がゼロの場合、非正則化補間に戻ります。

[1] https://projecteuclid.org/euclid.ss/1038425655.
