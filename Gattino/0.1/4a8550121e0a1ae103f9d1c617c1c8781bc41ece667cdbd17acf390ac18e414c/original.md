```julia
scatter -> ::AbstractContext
```

---

`scatter`, `line`, and `hist` are all high-level plotting functions used to create a `Context` and display features  from a data structure using a single function call. These all create a new context and call their respective `_plot!` function.      For example, `scatter` will call `scatter_plot!` – these functions may also be used to add plots to existing contexts.      The arguments for the `_plot!` equivalents are passed down from their plot creation functions. As a result, each dispatch      of `scatter` is a pass-through to the main dispatch of `scatter_plot!`, and arguments for that `Function` may be used. `width` and `height`

  * For a `scatter` plot, both `x` and `y` must be numerical.

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
# arguments are passed through to `scatter_plot!`, all of these key-word arguments can be used with `scatter`:
scatter_plot!(con::AbstractContext, x::Vector{<:Number}, y::Vector{<:Number}, features::Pair{String, <:AbstractVector} ...; 
    divisions::Int64 = 4, title::String = "", xlabel::String = "", ylabel::String = "", legend::Bool = true, colors::Vector{String} = Vector{String}(["#FF6633"]), 
    xmax::Number = maximum(x), xmin::Number = minimum(x), ymin::Number = minimum(y))

# for vectors
scatter(x::Vector{<:Any}, args ...; width::Int64 = 500, height::Int64 = 500, 
    keyargs ...)
# for dictionaries (secondary for data structures)
scatter(x::String, y::String, features::Dict{<:AbstractString, <:AbstractVector}, colors::Vector{String} = [randcolor() for e in 1:length(features)];
    width::Int64 = 500, height::Int64 = 500, keyargs ...)
# for data structures (binded to `names` and `eachcol`)
scatter(features::Any, x::Any = names(features)[1], y::Any = names(features)[2], 
    args ...; keyargs ...)
```
