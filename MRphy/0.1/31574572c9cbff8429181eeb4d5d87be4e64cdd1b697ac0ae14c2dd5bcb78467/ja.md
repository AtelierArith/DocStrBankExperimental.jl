```
RF0D = Quantity{<:Union{Real, Complex}, 𝐁}
```

磁気RFの型。[`Unitful.Quantity`](https://github.com/PainterQubits/Unitful.jl)に基づいています。

# 例:

```julia-repl
julia> ((1+1im)u"Gauss")::RF0D
1 + 1im Gauss
```
