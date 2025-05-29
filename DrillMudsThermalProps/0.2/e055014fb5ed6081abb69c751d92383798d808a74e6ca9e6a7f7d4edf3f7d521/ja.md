```
(F::Fluid)(P,T)
```

流体のすべてのサブタイプに対する一般的な関数。この関数は、`P` [Pa] および `T` [K] の点で適切なタイプのすべてのプロパティ計算を呼び出します。

# 引数

  * `P`: 圧力 [Pa].
  * `T`: 温度 [K].

# 出力

  * `output::NamedTuple`: 計算されたすべてのプロパティを含む名前付きタプル。

```julia
(
    ρ=density [kg/m³],
    κ=compressibility [1/Pa],
    β=expansivity [1/K],
    C=specific heat [J/kg K],
    k=thermal conductivity [W/m K],
    μ=dynamic viscosity [Pa s]
)
```
