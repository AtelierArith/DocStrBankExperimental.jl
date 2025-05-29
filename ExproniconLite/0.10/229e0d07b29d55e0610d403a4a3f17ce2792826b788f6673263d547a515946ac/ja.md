```
JLCall(ex::Expr)
```

Juliaの呼び出し式を`JLCall`に変換します。

# 例

```julia
ex = :(f(x, y; z=1))
jlcall = JLCall(ex)  # func=:f, args=[:x, :y], kwargs=[:(z=1)]を持つJLCallを作成します
```
