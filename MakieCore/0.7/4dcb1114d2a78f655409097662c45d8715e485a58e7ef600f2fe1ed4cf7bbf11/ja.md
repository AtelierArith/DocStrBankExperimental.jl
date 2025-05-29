```
Plot(args::Vararg{<:DataType,N})
```

`args`のシグネチャを表すPlot型を返します。例:

```julia
Plot(Vector{Point2f}) == Plot{plot, Tuple{<:Vector{Point2f}}}
```

これは、レシピマクロなしで`plot(mytype)`のためのレシピをより便利に作成するために使用できます:

```julia
struct MyType ... end

function Makie.plot!(plot::Plot(MyType))
    ...
end

plot(MyType(...))
```
