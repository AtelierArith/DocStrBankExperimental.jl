```
luaeval(expr::AbstractString)
```

Renoiseのスクリプト環境内でLua式を評価します。

# 例

```julia
luaeval("renoise.song().transport.bpm = 132")
```
