```julia
scatter -> ::AbstractContext
```

---

`scatter`、`line`、および `hist` はすべて、高レベルのプロット関数であり、`Context` を作成し、データ構造からの特徴を単一の関数呼び出しで表示するために使用されます。これらはすべて新しいコンテキストを作成し、それぞれの `_plot!` 関数を呼び出します。たとえば、`scatter` は `scatter_plot!` を呼び出します - これらの関数は、既存のコンテキストにプロットを追加するためにも使用できます。`_plot!` の同等物の引数は、プロット作成関数から渡されます。その結果、`scatter` の各ディスパッチは `scatter_plot!` のメインディスパッチへのパススルーであり、その `Function` の引数が使用される可能性があります。`width` および `height`

  * `scatter` プロットの場合、`x` と `y` は両方とも数値でなければなりません。

```example
using DataFrames
using Gattino

df = DataFrame("A" => [rand(1:1000) for x in 1:1000], "B" => [rand(5:20) for y in 1:1000], "C" => [rand(1:1000) for y in 1:1000], 
"D" => [rand(4:800) for y in 1:1000])
plot1 = scatter(df)
plot2 = scatter([1, 2, 3, 4, 5], [1, 2, 3, 4, 5], title = "straight line", width = 200, height = 200)
                   # x   y
plot3 = scatter(df, "C", "D", xlabel = "C", ylabel = "D")
plot4 = context(250, 250) do con::Context
    group(con, 100, 250, 0 => 0) do lastvis::Group
        group!(lastvis, "scatter1") do g::Group
            Gattino.scatter_plot!(g, [1, 2, 3], [1, 2, 3])
        end
    end
    group(con, 100, 250, 125 => 0) do lastvis::Group
        group!(lastvis, "hist1") do g::Group
            Gattino.hist_plot!(g, ["one", "two", "three", "four", "five"], [2, 7, 5, 5, 3])
        end
    end
end
result = vcat(hcat(plot1, plot2), hcat(plot3, plot4))
```

###### methods

```julia
# 引数は `scatter_plot!` に渡され、これらのキーワード引数はすべて `scatter` で使用できます：
scatter_plot!(con::AbstractContext, x::Vector{<:Number}, y::Vector{<:Number}, features::Pair{String, <:AbstractVector} ...; 
    divisions::Int64 = 4, title::String = "", xlabel::String = "", ylabel::String = "", legend::Bool = true, colors::Vector{String} = Vector{String}(["#FF6633"]), 
    xmax::Number = maximum(x), xmin::Number = minimum(x), ymin::Number = minimum(y))

# ベクターの場合
scatter(x::Vector{<:Any}, args ...; width::Int64 = 500, height::Int64 = 500, 
    keyargs ...)
# 辞書の場合（データ構造のためのセカンダリ）
scatter(x::String, y::String, features::Dict{<:AbstractString, <:AbstractVector}, colors::Vector{String} = [randcolor() for e in 1:length(features)];
    width::Int64 = 500, height::Int64 = 500, keyargs ...)
# データ構造の場合（`names` と `eachcol` にバインド）
scatter(features::Any, x::Any = names(features)[1], y::Any = names(features)[2], 
    args ...; keyargs ...)
```
