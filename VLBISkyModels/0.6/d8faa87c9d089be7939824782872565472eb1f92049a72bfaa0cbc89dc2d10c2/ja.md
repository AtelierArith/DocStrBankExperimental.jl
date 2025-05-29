```
convolved(m1::AbstractModel, m2::AbstractModel)
```

2つのモデルを畳み込んで合成 [`ConvolvedModel`](@ref VLBISkyModels.ConvolvedModel) を作成します。

```julia-repl
julia> convolved(m1, m2)
m1 = Ring()
```
