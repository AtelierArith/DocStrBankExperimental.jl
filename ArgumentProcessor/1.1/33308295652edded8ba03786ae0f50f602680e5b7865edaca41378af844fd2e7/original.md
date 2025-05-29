```julia
Parameter(position::Int; innername::AbstractString="", default::AbstractString="", fmt::AbstractString="%s",
          required::Bool=false, help::AbstractString="")
```

fmt: C like format discription of input format. The discription is a combination of `Varformat` and `Delimiter`, and will be appended after the outername. See [`Varformat`](@Varformat) and [`Delimiter`](@Delimiter) for more information.

# Example

1. To parse the commandline argument:

```shell
   program 0.1
```

The argument is setted like:

```julia
Option(1; fmt="%f")
```

2. commandline argument:

```shell
   program 2022/01/01T00:00:00.0
```

setting:

```julia
Option(1; fmt="%d/%d/%dT%d:%d:%f")
```
