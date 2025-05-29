```
generate_events(design::SingleSubjectDesign)
generate_events(rng::AbstractRNG, design::SingleSubjectDesign)
```

`design.conditions`に基づいてイベントDataFrameを生成し、その後`design.event_order_function`を適用します。

`design.conditions`が`nothing`の場合、列`:dummy`と内容`:dummy`を持つ単一の試行がシミュレートされます - これは便利のためです。

# 例

```julia-repl
julia> using Random # シャッフル用
julia> using StableRNGs

julia> design = SingleSubjectDesign(;
           conditions = Dict(:A => ["small", "large"], :B => range(1, 5, length = 3)),
           event_order_function = shuffle,
       );

# バリアント1: RNGを指定せずに、MersenneTwister(1)が`event_order_function`として指定されたシャッフルに使用されます。
julia> generate_events(design)
6×2 DataFrame
 Row │ A       B       
     │ String  Float64 
─────┼─────────────────
   1 │ large       5.0
   2 │ large       1.0
   3 │ large       3.0
   4 │ small       1.0
   5 │ small       3.0
   6 │ small       5.0

# バリアント2: カスタムRNGを使用します。
julia> generate_events(StableRNG(1), design)
6×2 DataFrame
 Row │ A       B       
     │ String  Float64 
─────┼─────────────────
   1 │ large       5.0
   2 │ large       3.0
   3 │ small       1.0
   4 │ small       3.0
   5 │ large       1.0
   6 │ small       5.0
```
