```julia
julia2json(str::String) -> Dict{Symbol, Any}

```

julia2jsonは、Juliaの式をJSON文字列に変換します。

# 例:

julia2jsonは、文字列または式を受け入れます。

```julia
ex = "function f(x)
x + 1
end" |> julia2json
JSON3.pretty(file, ex)
```

```julia
ex = :(function f(x)
x + 1
end) |> julia2json
JSON3.pretty(file, ex)
```

julia2jsonはマクロとしても使用できます。

```julia
s = @julia2json function f(x)
    x + 1
end
JSON3.pretty(file, s)
```
