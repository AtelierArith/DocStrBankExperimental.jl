```
TidalForcing(; x_amplitude,
               y_amplitude,
               period = 12.3782216453hours,
               nodal_time = 0.,
               x_lag = 0.,
               y_lag = 0.,
               coriolis = nothing)
```

`Tide`の便利なコンストラクタで、強制力を事前にラップして返します。

# キーワード引数

  * `x_amplitude`: x方向の潮汐振幅
  * `y_amplitude`: y方向の潮汐振幅
  * `period`: 潮汐周期（M2潮汐の周期がデフォルト）
  * `nodal_time`: ピークフローが発生する時間
  * `x_lag`: x方向の潮汐成分の位相遅れ
  * `y_lag`: y方向の潮汐成分の位相遅れ
  * `coriolis`: コリオリパラメータのモデル

# 例

```jldoctest
julia> using Walrus: TidalForcing

julia> tidal_forcing = TidalForcing(x_amplitude = 0.1, y_amplitude = 0.)
(u = DiscreteForcing{Val{:x}}
├── func: (::Tide{Float64, Nothing}) (generic function with 2 methods)
└── parameters: Val{:x}(), v = DiscreteForcing{Val{:y}}
├── func: (::Tide{Float64, Nothing}) (generic function with 2 methods)
└── parameters: Val{:y}())
```
