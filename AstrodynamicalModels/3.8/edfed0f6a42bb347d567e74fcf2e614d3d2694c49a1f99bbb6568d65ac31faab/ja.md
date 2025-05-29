```julia
CR3BFunction(; stm, name, kwargs...)

```

CR3Bダイナミクスのための`ODEFunction`を返します。

状態の順序は次の通りです: `[μ]`。

パラメータの順序は次の通りです: `[μ]`。

# 拡張ヘルプ

### 使用法

`stm`および`name`キーワード引数は`CR3B`に渡されます。他のすべてのキーワード引数は直接`SciMLBase.ODEFunction`に渡されます。

```julia
f = CR3BFunction(; stm=false, jac=true)
let u = randn(6), p = randn(1), t = 0
    f(u, p, t)
end
```
