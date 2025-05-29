```julia
Option(innername::AbstractString; outername::AbstractString="", abbr::AbstractString="",
       default::AbstractString="", fmt::AbstractString="%s", required::Bool=false, help::AbstractString="")
```

fmt: C like format discription of input format. The discription is a combination of `Varformat` and `Delimiter`, and will be appended after the outername. See [`Varformat`](@Varformat) and [`Delimiter`](@Delimiter) for more information.

# Example

To parse the commandline argument:

```shell
program --test=0.1/0.2
```

The argument is setted like:

```julia
Option("test"; fmt="=%f/%f")
```
