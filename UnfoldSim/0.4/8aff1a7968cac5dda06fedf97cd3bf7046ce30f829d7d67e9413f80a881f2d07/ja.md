```
RepeatDesign{T} <: AbstractDesign
```

デザインを繰り返し（および対応するイベントのDataFrame）複数回実行して、繰り返し記録された試行を模倣します。

ヒント: [`generate_events`](@ref) 関数を使用して、結果のデータフレームを確認してください。`RepeatDesign`で`event_order_function`（例: `shuffle`）を使用する場合、対応するRNGは繰り返しの間で共有され、各繰り返しのために深くコピーされることはありません。その結果、イベントの順序は各繰り返しで異なります。

# フィールド

  * `design::T`: 繰り返すべき実験デザイン。
  * `repeat::Int = 1`: 繰り返しの回数。

# 例

```julia-repl
julia> using StableRNGs # `generate_events` 関数を再現可能な方法で使用するため

julia> design_once =
           SingleSubjectDesign(;
               conditions = Dict(
                   :stimulus_type => ["natural", "artificial"],
                   :contrast_level => range(0, 1, length = 2),
               ),
               event_order_function = shuffle,
           );

julia> generate_events(StableRNG(1), design_once)
4×2 DataFrame
 Row │ contrast_level  stimulus_type 
     │ Float64         String        
─────┼───────────────────────────────
   1 │            1.0  natural
   2 │            1.0  artificial
   3 │            0.0  natural
   4 │            0.0  artificial

julia> design = RepeatDesign(design_once, 2)
RepeatDesign{SingleSubjectDesign}
  design: SingleSubjectDesign
  repeat: Int64 2

julia> generate_events(StableRNG(1), design)
8×2 DataFrame
 Row │ contrast_level  stimulus_type 
     │ Float64         String        
─────┼───────────────────────────────
   1 │            1.0  natural
   2 │            1.0  artificial
   3 │            0.0  natural
   4 │            0.0  artificial
   5 │            1.0  artificial
   6 │            0.0  natural
   7 │            1.0  natural
   8 │            0.0  artificial
```

他にも [`SingleSubjectDesign`](@ref), [`MultiSubjectDesign`](@ref) を参照してください。
