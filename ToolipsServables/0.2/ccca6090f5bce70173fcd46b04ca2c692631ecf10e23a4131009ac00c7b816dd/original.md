```julia
write!(io, args ...) -> _
```

The `write` `Function` is used to `write!` `Servables` to  a `<: IO` or a `String`.

```julia
write!(io::IO, servables::Servable ...) -> ::Nothing
write!(io::String, servables::Servable ...) -> ::String
```

```julia
using ToolipsServables
# write candidate
str_sample = ""
buff = IOBuffer()

# templating
mycomp = div("example", align = "center")

# writing
write!(buff, mycomp)
str_sample = write!(str_sample, mycomp)
```

```example
# writing a file
file::File{:txt} = File("texts/example.txt")

rawfile = write!("", file)
```
