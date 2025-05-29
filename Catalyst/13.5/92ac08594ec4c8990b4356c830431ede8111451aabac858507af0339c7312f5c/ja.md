```
oderatelaw(rx; combinatoric_ratelaw=true)
```

与えられた [`Reaction`](@ref) に対して、反応の生成された ODE に使用される記号反応速度法則を返します。次のような反応が定義されている場合

`k*X*Y, X+Z --> 2X + Y`

返される式は `k*X(t)^2*Y(t)*Z(t)` になります。次の形式の反応の場合

`k, 2X+3Y --> Z`

返される式は `k * (X(t)^2/2) * (Y(t)^3/6)` になります。

注意:

  * アロケート
  * `combinatoric_ratelaw=true` は、速度法則を計算する際に階乗スケーリング係数を使用します。つまり、`2S -> 0` の場合、速度は `k` であり、速度法則は `k*S^2/2!` になります。`combinatoric_ratelaw=false` の場合、速度法則は `k*S^2` になり、スケーリング係数は無視されます。
