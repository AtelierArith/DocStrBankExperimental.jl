```julia
`line` -> ::AbstractContext
```

`line`、`scatter`、および `hist` はすべて、高レベルのプロット関数であり、単一の関数呼び出しを使用してデータ構造からの特徴を表示する `Context` を作成するために使用されます。`line` は、他のプロット関数と同様に、`line_plot!` と同じ引数を取ります。`line` プロットは、数値的および非数値的な X の両方を使用して作成できます。

```julia

```

###### methods

```julia
# from vectors
line(x::Vector{<:Any}, y::Vector{<:Any}, args ...; keyargs ...)
line(x::String, y::String, features::Dict{String, <:AbstractVector}, colors::Vector{String} = [randcolor() for e in 1:length(features)]; width::Int64 = 500, 
    height::Int64 = 500, keyargs ...)
line(features::Any, x::Any = names(features)[1], y::Any = names(features)[2], args ...; keyargs ...)
```
