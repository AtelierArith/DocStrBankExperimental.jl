```
function inject_chromosome!(brkga_data::BrkgaData,
                            chromosome::Array{Float64, 1},
                            population_index::Int64,
                            position::Int64,
                            fitness::Float64 = Inf)
```

`chromosome`とその`fitness`を`position`の場所にある`population_index`の集団に注入します。fitnessが提供されていない場合（`fitness = Inf`）、`chromosome`に対してデコーディングが行われます。クロモソームが注入されると、集団はクロモソームのフィットネスに基づいて再ソートされます。

# 例外をスローします

  * `ErrorException`: [`initialize!`](@ref)が事前に呼び出されていない場合。
  * `ArgumentError`: `population_index < 1`または`population_index > num_independent_populations`の場合。
  * `ArgumentError`: `position < 1`または`position > population_size`の場合。
  * `ArgumentError`: `lenght(chromosome) != chromosome_size`の場合。

```
