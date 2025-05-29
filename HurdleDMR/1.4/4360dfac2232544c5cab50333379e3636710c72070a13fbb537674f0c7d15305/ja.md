```
fit(InclusionRepetition,M,f,df; fpos=Xpos, <キーワード引数>)
```

データフレームと2つの式を受け取ります。1つは各モデル部分用です。それ以外は[`fit(::InclusionRepetition)`](@ref)と同じ引数です。

# 例

```julia
  fit(InclusionRepetition,GeneralizedLinearModel,@formula(y ~ x1*x2), df; fpos=@formula(y ~ x1*x2+x3))
```
