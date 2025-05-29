```
bseries(rk::RungeKuttaMethod, order)
bseries(A::AbstractMatrix, b::AbstractVector, c::AbstractVector, order)
```

Runge-Kutta法 `rk` のB系列を、指定された整数 `order` までのButcher係数 `A, b, c` で計算します。

!!! note "基本微分による正規化"
    このメソッドによって返されるB系列の係数は、時間ステップのべき乗を根付き木の `symmetry` で割り、入力ベクトル場 $f$ の対応する基本微分で掛ける必要があります。詳細は [`evaluate`](@ref) を参照してください。

