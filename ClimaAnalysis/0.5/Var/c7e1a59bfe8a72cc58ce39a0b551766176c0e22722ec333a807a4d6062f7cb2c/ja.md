```
Var.convert_units(var, new_units; conversion_function = nothing)
```

物理単位を `var` から `new_units` に変換した新しい `OutputVar` を返します。可能な場合に限ります。

自動変換は、`var` と `new_units` の両方の単位が解析可能な場合に行われます。`var` に単位がない場合（[`Var.has_units`](@ref) も参照）や、解析可能な単位がない場合は、変換関数 `conversion_function` が必要です。

`conversion_function` は、1つのデータポイントを受け取り、変換された値を返す関数でなければなりません。

解析可能であるとは、`Unitful.uparse` がその式を解析できることを意味します。詳細については、[Unitful.jl](https://painterqubits.github.io/Unitful.jl/stable/) のドキュメントを参照してください。

# 例

メートル毎秒の単位を持つトリビアルな1D `OutputVar` を設定し、自動的にセンチメートル毎秒に変換してみましょう。

```jldoctest example1
julia> values = 0:100.0 |> collect;

julia> data = copy(values);

julia> attribs = Dict("long_name" => "speed", "units" => "m/s");

julia> dim_attribs = Dict{String, Dict}();

julia> var = ClimaAnalysis.OutputVar(attribs, Dict("distance" => values), dim_attribs, data);

julia> ClimaAnalysis.has_units(var)
true

julia> var_cms = ClimaAnalysis.convert_units(var, "cm/s");

julia> extrema(var_cms.data)
(0.0, 10000.0)
```

すべての単位が適切に解析できるわけではありません。たとえば、`bob=5lol` と仮定します。

```jldoctest example1
julia> attribs = Dict("long_name" => "speed", "units" => "bob/s");

julia> var_bob = ClimaAnalysis.OutputVar(attribs, Dict("distance" => values), dim_attribs, data);

julia> var_lols = ClimaAnalysis.convert_units(var, "lol/s", conversion_function = (x) -> 5x);

julia> extrema(var_lols.data)
(0.0, 500.0)
```

`conversion_function` を指定しないとエラーが発生します。
