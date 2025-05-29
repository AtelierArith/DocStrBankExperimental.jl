```
factor_absolute(f::QQMPolyRingElem)
```

fのQ[X]におけるCでの因数分解を計算し、最初の要素が主係数で、次にQ[X]における各不可約因子のペアを含む配列を返します。

  * タプルを含む

      * 数体における不可約因子
      * この体における他のすべての共役因子の積
  * 重複度。

Qにおける各不可約因子には、この因子がさらに分裂する（最小の）数体が1つ存在します（おそらくQ）。この場合、この体におけるすべての因子はガロワ共役です。巨大な分裂体を作成しないために、1つの因子と共役の積のみが返されます。

# 例

```julia
julia> Qx, (x, y) = polynomial_ring(QQ, ["x", "y"]);

julia> f = (x^3+5*y^3)*(x^2+2*y^2);

julia> z = factor_absolute(f)

3-element Vector{Any}:
                                                                            1
                AbstractAlgebra.Generic.MPoly{AbsSimpleNumFieldElem}[x + _a*y, x - _a*y] => 1
 AbstractAlgebra.Generic.MPoly{AbsSimpleNumFieldElem}[x + _a*y, x^2 - _a*x*y + _a^2*y^2] => 1

julia> z[2][1][1]
x + _a*y

julia> base_ring(ans)
Number field over Rational Field with defining polynomial x^2 + 2

julia> base_ring(z[3][1][1])
Number field over Rational Field with defining polynomial x^3 - 5
```
