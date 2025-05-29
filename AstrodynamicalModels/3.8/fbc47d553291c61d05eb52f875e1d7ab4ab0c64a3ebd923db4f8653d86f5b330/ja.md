```julia
R2BFunction(; stm, name, kwargs...)

```

R2Bダイナミクスのための`ODEFunction`を返します。

状態の順序は次の通りです: `[x, y, z, ẋ, ẏ, ż]`。

パラメータの順序は次の通りです: `[μ]`。

# 拡張ヘルプ

### 使用法

`stm`および`name`キーワード引数は`R2B`に渡されます。他のすべてのキーワード引数は直接`SciMLBase.ODEFunction`に渡されます。

```julia
f = R2BFunction(; stm=false, name=:R2B, jac=true)
let u = randn(6), p = randn(1), t = 0
    f(u, p, t)
end
```
