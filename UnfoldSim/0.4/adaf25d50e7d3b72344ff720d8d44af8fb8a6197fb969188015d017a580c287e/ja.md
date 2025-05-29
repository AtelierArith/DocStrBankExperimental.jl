```
シミュレーション
```

シミュレーションのすべての「成分」とそのパラメータを格納するための型。

ユーザーによって作成されるか、必要な「成分」とともに[`simulate`](@ref)関数を呼び出すと自動的に作成されます。ヒント: `subtypes`関数を使用して、実装された「成分」の概要を取得します。例えば、`subtypes(AbstractDesign)`。

# フィールド

  * `design::AbstractDesign`: 実験デザイン。
  * `components::Vector{AbstractComponent}`: イベントの応答関数（例: EEGにおけるERP形状）。
  * `onset::AbstractOnset`: 発生間隔の距離分布。
  * `noisetype::AbstractNoise`: ノイズタイプ。

# 例

```julia-repl
julia> design = SingleSubjectDesign(; conditions = Dict(:stimulus_type => ["natural", "artificial"]));

julia> component = LinearModelComponent(;
           basis = p100(),
           formula = @formula(0 ~ 1 + stimulus_type),
           β = [2, 3],
       );

julia> onset = UniformOnset();

julia> noise = PinkNoise();

julia> simulation = Simulation(design, component, onset, noise);

julia> using StableRNGs

julia> data, events = simulate(StableRNG(1), simulation);

julia> events
2×2 DataFrame
 Row │ stimulus_type  latency 
     │ String         Int64   
─────┼────────────────────────
   1 │ natural             20
   2 │ artificial          70

julia> data
85-element Vector{Float64}:
  0.8596261232522926
  1.1657369535500595
  0.9595228616486761
  ⋮
  0.9925202143746904
  0.2390652543395527
 -0.11672523788068771
```
