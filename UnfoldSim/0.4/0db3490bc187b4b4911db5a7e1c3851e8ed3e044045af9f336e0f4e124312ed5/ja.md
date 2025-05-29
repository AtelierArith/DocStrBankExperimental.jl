```
generate_events(design::MultiSubjectDesign)
generate_events(rng::AbstractRNG, design::MultiSubjectDesign)
```

`MixedModelsSim.jl`の`simdat_crossed`関数に従ってイベントのDataFrameを生成します。

その後、`design.event_order_function`を適用し、最後に`:subject`でソートします。 注意: 条件に`dv`という名前を付けることはできません。これはMixedModelsSim / MixedModels内でダミーの左側として使用されています。

# 例

```julia-repl
julia> using Random # シャッフル用
julia> using StableRNGs

julia> design = MultiSubjectDesign(;
                       n_items = 4,
                       n_subjects = 5,
                       both_within = Dict(:condition => ["red", "green"]),
                       event_order_function = shuffle,
                       );

julia> generate_events(StableRNG(1), design)
40×3 DataFrame
 Row │ subject  item    condition 
     │ String   String  String    
─────┼────────────────────────────
   1 │ S1       I2      red
   2 │ S1       I2      green
   3 │ S1       I3      green
  ⋮  │    ⋮       ⋮         ⋮
  38 │ S5       I3      red
  39 │ S5       I2      red
  40 │ S5       I4      green
                   34 rows omitted
```
