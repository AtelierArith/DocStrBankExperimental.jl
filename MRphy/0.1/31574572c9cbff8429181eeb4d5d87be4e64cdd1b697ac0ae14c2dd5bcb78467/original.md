```
RF0D = Quantity{<:Union{Real, Complex}, 𝐁}
```

Type of magnetic RF. Based on [`Unitful.Quantity`](https://github.com/PainterQubits/Unitful.jl).

# Examples:

```julia-repl
julia> ((1+1im)u"Gauss")::RF0D
1 + 1im Gauss
```
