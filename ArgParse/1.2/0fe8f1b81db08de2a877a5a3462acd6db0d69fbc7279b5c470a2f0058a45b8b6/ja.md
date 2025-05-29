```
add_arg_table!(settings, [arg_name [,arg_options]]...)
```

この関数はマクロ版[`@add_arg_table!`](@ref)に非常に似ています。その構文はより厳格で、タプルやブロックは許可されておらず、引数オプションは明示的に`Dict`オブジェクトとして指定されます。しかし、マクロを含まないため、他の点でより柔軟性があります。例えば、`arg_name`のエントリは明示的である必要はなく、`String`または`Vector{String}`に評価されるものであれば何でも構いません。

例:

```julia
add_arg_table!(settings,
    ["--opt1", "-o"],
    Dict(
        :help => "an option with an argument"
    ),
    "--opt2",
    "arg1",
    Dict(
        :help => "a positional argument"
        :required => true
    ))
```
