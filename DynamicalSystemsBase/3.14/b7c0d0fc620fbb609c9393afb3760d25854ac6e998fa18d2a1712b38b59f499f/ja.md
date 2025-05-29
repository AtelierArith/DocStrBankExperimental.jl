```
ProjectedDynamicalSystem <: DynamicalSystem
ProjectedDynamicalSystem(ds::DynamicalSystem, projection, complete_state)
```

既存の `ds` の（投影された）空間への投影を表す動的システムです。

`projection` は投影された空間を定義します。もし `projection isa AbstractVector{Int}` であれば、投影された空間は単に `projection` が含む変数のインデックスです。それ以外の場合、`projection` は元のシステム `ds` の状態を与えられたときに、投影された空間の状態を返す任意の関数であることができます。この場合、投影された空間は元の空間と同じか、さらには高次元であることも可能です。

`complete_state` は投影された状態から元のシステムの状態を生成します。`complete_state` は常に、投影された状態を与えられたときに元の空間の状態を返す関数であることができます。しかし、もし `projection isa AbstractVector{Int}` であれば、`complete_state` はシステムの*残りの*変数の値を含むベクトルでも構いません。すなわち、投影された空間に*含まれていない*変数です。この場合、投影された空間は元の空間よりも低次元である必要があります。

`ProjectedDynamicalSystem` は可逆な投影を必要としないことに注意してください。`complete_state` は [`reinit!`](@ref) の間だけ使用されます。`ProjectedDynamicalSystem` は実際には `ds` のかなり単純なラッパーであり、元の状態空間で通常通りステップを進め、最後のステップとしてのみ投影を行います。例えば、[`current_state`](@ref) の間にです。

## 例

ケース 1: 5次元システムを最後の2次元に投影します。

```julia
ds = Systems.lorenz96(5)
projection = [4, 5]
complete_state = [0.0, 0.0, 0.0] # 最後の2次元の平面での完成状態
prods = ProjectedDynamicalSystem(ds, projection, complete_state)
reinit!(prods, [0.2, 0.4])
step!(prods)
current_state(prods)
```

ケース 2: 状態の一般的な関数へのカスタム投影。

```julia
ds = Systems.lorenz96(5)
projection(u) = [sum(u), sqrt(u[1]^2 + u[2]^2)]
complete_state(y) = repeat([y[1]/5], 5)
prods = # 上記の例と同じ...
```
