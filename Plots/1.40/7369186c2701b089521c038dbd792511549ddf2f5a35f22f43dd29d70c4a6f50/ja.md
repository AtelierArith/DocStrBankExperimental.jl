```
P_str(s)
```

(Unitful 拡張のみ)。レシピパスから保護される文字列を作成します。

例：

```julia
julia> using Unitful
julia> plot([0,1]u"m", [1,2]u"m/s^2", xlabel=P"This label will NOT display units")
julia> plot([0,1]u"m", [1,2]u"m/s^2", xlabel="This label will display units")
```
