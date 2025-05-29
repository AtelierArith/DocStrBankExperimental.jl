```julia
julia2json(str::String) -> Dict{Symbol, Any}

```

julia2json converts a Julia expression to a JSON string.

# Examples:

julia2json accepts a string or an expression.

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

julia2json can also be used as a macro

```julia
s = @julia2json function f(x)
    x + 1
end
JSON3.pretty(file, s)
```
