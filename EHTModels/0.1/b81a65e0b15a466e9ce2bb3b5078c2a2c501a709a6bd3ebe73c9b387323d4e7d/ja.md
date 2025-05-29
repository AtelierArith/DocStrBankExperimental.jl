```
convolved(m1::AbstractModel, m2::AbstractModel)
```

2つのモデルを畳み込んで合成 [`ConvolvedModel`](@ref Comrade.ConvolvedModel) を作成します。

```julia-repl
julia> m1 = Ring()
julia> m2 = Disk()
julia> convolved(m1, m2)
```
