```
PoincareMap <: DiscreteTimeDynamicalSystem
PoincareMap(ds::CoupledODEs, plane; kwargs...) → pmap
```

与えられた連続時間 `ds` のポアンカレ写像[^DatserisParlitz2022] を反復する離散時間力学系です。この写像は、`plane` 引数によって定義されるポアンカレ断面上の点の列として定義されます。

`pmap` を反復することは、`pmap` で参照される `ds` をも変化させます。

関連項目としては [`StroboscopicMap`](@ref)、[`poincaresos`](@ref) があります。

## キーワード引数

  * `direction = -1`: `sign(direction)` を持つ交差のみが断面に属すると見なされます。負の方向は、$b$ より小さい値から $b$ より大きい値に移動することを意味します。
  * `u0 = nothing`: 初期状態を指定します。`nothing` の場合は `current_state(ds)` になります。
  * `rootkw = (xrtol = 1e-6, atol = 1e-8)`: [Roots.jl](https://github.com/JuliaMath/Roots.jl) の `find_zero` に渡されるキーワード引数の `NamedTuple` です。
  * `Tmax = 1e3`: 引数 `Tmax` は、積分器が無限の時間進化するのではなく終了できるように存在します。これは、定義が不明な超平面や固定点への収束のために、反復が永遠に続く場合を避けるためです。1 回の `step!` の間にシステムが `Tmax` を超えて進化した場合、`step!(pmap)` は終了し、エラーになります。

## 説明

ポアンカレ断面は、任意の多様体との間で軌道が持つ連続的な横断を定義しますが、ここでは多様体は超平面でなければなりません。`PoincareMap` は断面の交差を反復します。

もし `ds` の状態が $\mathbf{u} = (u_1, \ldots, u_D)$ であれば、超平面を定義する方程式は次のようになります。

$$
a_1u_1 + \dots + a_Du_D = \mathbf{a}\cdot\mathbf{u}=b
$$

ここで、$\mathbf{a}, b$ は超平面のパラメータです。

コードでは、`plane` は次のいずれかです：

  * `Tuple{Int, <: Real}` のように `(j, r)`：この平面は、システムの `j` 番目の変数が値 `r` に等しいときに定義されます。
  * 長さ `D+1` のベクトル。ベクトルの最初の `D` 要素は $\mathbf{a}$ に対応し、最後の要素は $b$ です。

`PoincareMap` は `ds`、DifferentialEquations.jl からの高次補間、および Roots.jl からの根探索を使用して、断面の高精度な推定を作成します。

`PoincareMap` は次の調整を伴って [`DynamicalSystem`](@ref) インターフェースに従います：

1. `dimension(pmap) == dimension(ds)` ですが、ポアンカレ写像は実際には1次元少ないです。
2. [`StroboscopicMap`](@ref) のように、時間は離散であり、断面上の反復をカウントします。[`initial_time`](@ref) は常に `0` で、[`current_time`](@ref) は現在の反復番号です。
3. 新しい関数 [`current_crossing_time`](@ref) は、超平面の最新の交差に対応する実時間を返します。超平面上の対応する状態は、期待通り `current_state(pmap)` です。
4. `plane` が `Tuple{Int, <:Real}` の特別な場合には、長さ `D-1` の入力状態を持つ特別な `reinit!` メソッドが許可されます。つまり、超平面上にすでにある縮小状態が `D` 次元の状態に変換されます。
5. `initial_state(pmap)` はマップの初期状態を返します。これは `u0` ではなく、`u0` はポアンカレ平面に存在するまで前方に進化します。
6. `reinit!` 関数では、`t0` キーワードは連続時間力学系の開始時間を示します。`PoincareMap` の開始時間は定義上常に 0 です。

## 例

```julia
using DynamicalSystemsBase, PredefinedDynamicalSystems
ds = Systems.rikitake(zeros(3); μ = 0.47, α = 1.0)
pmap = poincaremap(ds, (3, 0.0))
step!(pmap)
next_state_on_psos = current_state(pmap)
```

[^DatserisParlitz2022]: Datseris & Parlitz 2022, *Nonlinear Dynamics: A Concise Introduction Interlaced with Code*, [Springer Nature, Undergrad. Lect. Notes In Physics](https://doi.org/10.1007/978-3-030-91032-7)
