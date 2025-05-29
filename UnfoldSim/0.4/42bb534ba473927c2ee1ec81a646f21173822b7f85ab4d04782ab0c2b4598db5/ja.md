```
SingleSubjectDesign <: AbstractDesign
```

単一被験者の実験デザインを指定するための型（与えられた条件に基づく）。

ヒント: [`generate_events`](@ref) 関数を使用して結果のデータフレームを確認してください。 `generate_events([rng, ]design)` の出力の試行/行数は、あなたの `conditions` の完全な因子の数に依存します。 繰り返しの数を増やすには、例えば 5 回、単に `RepeatDesign(SingleSubjectDesign(...), 5)` を使用してください。 条件が省略されるか（または `nothing` に設定されると）、列 `:dummy` と内容 `:dummy` で単一の試行がシミュレートされます - これは便利のためです。

# フィールド

  * `conditions::Dict{Symbol,Vector}`: 実験条件、例: `Dict(:A => ["a_small","a_big"], :B => ["b_tiny","b_large"])`。
  * `event_order_function = (rng, x) -> x`: `sort` を指定してソートしたり、`shuffle` を提供してシャッフルしたり、インターフェース `(rng, x) -> my_shuffle(rng,x)` に従ったカスタム関数を提供するために使用できます。 デフォルトは同一関数であり、すなわちイベントの順序を変更しません。

# 例

```julia-repl
julia> using StableRNGs # `generate_events` 関数を再現可能な方法で使用するため

julia> design =
           SingleSubjectDesign(;
               conditions = Dict(
                   :stimulus_type => ["natural", "artificial"],
                   :contrast_level => range(0, 1, length = 5),
               ),
           )
SingleSubjectDesign
  conditions: Dict{Symbol, Vector}
  event_order_function: #10 (function of type UnfoldSim.var"#10#14")

julia> generate_events(StableRNG(1), design)
10×2 DataFrame
 Row │ contrast_level  stimulus_type 
     │ Float64         String        
─────┼───────────────────────────────
   1 │           0.0   natural
   2 │           0.25  natural
   3 │           0.5   natural
  ⋮  │       ⋮               ⋮
   8 │           0.5   artificial
   9 │           0.75  artificial
  10 │           1.0   artificial
                       4 rows omitted
```

他にも [`MultiSubjectDesign`](@ref)、[`RepeatDesign`](@ref) を参照してください。
