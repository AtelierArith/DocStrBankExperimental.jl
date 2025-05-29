```julia
tmd(name::String, md::String = "", args::Pair{String, <:Any} ...; args ...) -> ::Component{:div}
```

Creates a `Component` directly from a raw markdown String. The `Component's` children will be  the markdown provided rendered to HTML.

```example
mymd = "# hello\n **this** is markdown"

comp = tmd("mygreeting", mymd)
```
