```
graphsummary([io], graph, extracolumns...; [inputhl], [outputhl], kwargs...)
```

Prints a summary table of `graph` to `io` using `PrettyTables.pretty_table`.

Extra columns can be added to the table by providing any number of `extracolumns` which can be one of the following:

  * a function (or any callable object) which takes a vertex as input and returns the column content
  * a `Pair` where the first element is the column name and the other element is what previous bullet describes

The keyword arguments `inputhl` (default `crayon"fg:black bg:249"`) and `outputhl` (default `inputhl`) can be used to set the highlighting of the inputs and outputs to `graph` respectively. If set to `nothing` no special highlighting will be used.

All other keyword arguments are forwarded to `PrettyTables.pretty_table`. Note that this allows for overriding the default formatting, alignment and highlighting.

!!! warning "API Stability"
    While this function is part of the public API for natural reasons, the exact shape of its output shall not be considered stable.

    `Base.show` for `CompGraph`s just calls this function. This might change in the future.


### Examples

```jldoctest
julia> using NaiveNASlib

julia> g = let 
            v1 = "v1" >> inputvertex("in1", 1) + inputvertex("in2", 1)
            v2 = invariantvertex("v2", sin, v1)
            v3 = conc("v3", v1, v2; dims=1) 
            CompGraph(inputs(v1), v3)
        end;

julia> graphsummary(g)
┌────────────────┬───────────┬────────────────┬───────────────────┐
│ Graph Position │ Vertex Nr │ Input Vertices │ Op                │
├────────────────┼───────────┼────────────────┼───────────────────┤
│ Input          │ 1         │                │                   │
│ Input          │ 2         │                │                   │
│ Hidden         │ 3         │ 1,2            │ + (element wise)  │
│ Hidden         │ 4         │ 3              │ sin               │
│ Output         │ 5         │ 3,4            │ cat(x..., dims=1) │
└────────────────┴───────────┴────────────────┴───────────────────┘

julia> graphsummary(g, name, "input sizes" => nin, "output sizes" => nout)
┌────────────────┬───────────┬────────────────┬───────────────────┬──────┬─────────────┬──────────────┐
│ Graph Position │ Vertex Nr │ Input Vertices │ Op                │ Name │ input sizes │ output sizes │
├────────────────┼───────────┼────────────────┼───────────────────┼──────┼─────────────┼──────────────┤
│ Input          │ 1         │                │                   │ in1  │             │ 1            │
│ Input          │ 2         │                │                   │ in2  │             │ 1            │
│ Hidden         │ 3         │ 1,2            │ + (element wise)  │ v1   │ 1,1         │ 1            │
│ Hidden         │ 4         │ 3              │ sin               │ v2   │ 1           │ 1            │
│ Output         │ 5         │ 3,4            │ cat(x..., dims=1) │ v3   │ 1,1         │ 2            │
└────────────────┴───────────┴────────────────┴───────────────────┴──────┴─────────────┴──────────────┘
```
