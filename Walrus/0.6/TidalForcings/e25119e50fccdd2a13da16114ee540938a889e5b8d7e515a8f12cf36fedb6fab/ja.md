```
Tide(; x_amplitude, 
       y_amplitude, 
       period = 12.3782216453hours,
       nodal_time = 0., 
       x_lag = 0., 
       y_lag = 0.,
       coriolis = nothing)
```

M2潮汐のデフォルトパラメータを持つ潮汐強制のモデルを設定します。

# キーワード引数

  * `x_amplitude`: x方向の潮汐振幅
  * `y_amplitude`: y方向の潮汐振幅
  * `period`: 潮汐周期（M2潮汐のものがデフォルト）
  * `nodal_time`: ピークフローが発生する時間
  * `x_lag`: x方向の潮汐成分の位相遅れ
  * `y_lag`: y方向の潮汐成分の位相遅れ
  * `coriolis`: コリオリパラメータのモデル

# 例

```jldoctest
julia> using Walrus: Tide

julia> using Oceananigans

julia> tide = Tide(x_amplitude = 0.1, y_amplitude = 0.)
(::Tide{Float64, Nothing}) (generic function with 2 methods)
julia> forcing = (u = Forcing(tide, parameters = Val(:x), discrete_form = true),
                  v = Forcing(tide, parameters = Val(:y), discrete_form = true))
(u = DiscreteForcing{Val{:x}}
├── func: (::Tide{Float64, Nothing}) (generic function with 2 methods)
└── parameters: Val{:x}(), v = DiscreteForcing{Val{:y}}
├── func: (::Tide{Float64, Nothing}) (generic function with 2 methods)
└── parameters: Val{:y}())
```
