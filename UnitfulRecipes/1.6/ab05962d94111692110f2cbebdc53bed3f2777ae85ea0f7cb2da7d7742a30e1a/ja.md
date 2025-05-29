```
P_str(s)
```

レシピのパスから保護される文字列を作成します。

例:

```julia
julia> plot(rand(10)*u"m", xlabel=P"This label is protected")

julia> plot(rand(10)*u"m", xlabel=P"This label is not")
```
