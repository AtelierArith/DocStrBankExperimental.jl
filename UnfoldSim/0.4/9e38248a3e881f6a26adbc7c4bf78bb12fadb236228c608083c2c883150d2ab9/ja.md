```
simulate_onsets(rng, onset::AbstractOnset, simulation::Simulation)
```

`simulate_interonset_distances`を呼び出してイベント間の距離を生成し、それを合計してサンプルの実際の遅延を生成します。

この関数は主に`simulate`関数呼び出しの文脈で内部使用のために設計されています。

また、最初にサンプリングされたオンセットが0の場合にインデックスの問題を避けるため、オンセットの累積は1から始まります。

# 引数

  * `rng`: プロセスを再現可能にするための乱数生成器（RNG）。
  * `onset::AbstractOnset`: `simulate_interonset_distances`に渡されるイベント間の距離分布。
  * `simulation::Simulation`: 設計、コンポーネント、イベント間の距離分布、ノイズを含むシミュレーションオブジェクト。

# 戻り値

# 例

```julia-repl
# シミュレーションオブジェクトを作成
julia> design_single = SingleSubjectDesign(;
           conditions = Dict(
               :stimulus_type => ["natural", "artificial"],
               :contrast_level => range(0, 1, length = 3),
           ),
       );

julia> p1_component = LinearModelComponent(; basis = p100(), formula = @formula(0 ~ 1), β = [5]);

julia> simulation = Simulation(design_single, p1_component, UniformOnset(), NoNoise());

julia> using StableRNGs

# このシミュレーションのためにオンセットをシミュレート
julia> simulate_onsets(StableRNG(1), simulation.onset, simulation)
6-element Vector{Int64}:
  20
  70
  97
 110
 150
 182
```

[`simulate_interonset_distances`](@ref)も参照してください。
