```julia
GTMFunction(; stm, name, kwargs...)

```

`GTM`ダイナミクスに対応した`DifferentialEquations`互換の`ODEFunction`を返します。`stm`および`name`キーワード引数は`GTM`に渡されます。他のすべてのキーワード引数は直接`ODEFunction`に渡されます。

# 拡張ヘルプ

## 使用法

この`ODEFunction`出力には、インプレースメソッドを含むいくつかのメソッドがあります！関数シグネチャは`ModelingToolkit`および`DifferentialEquations`の規約に従います。

```julia
f = GTMFunction()
let u = randn(4), p = randn(2), t = rand()
    f(u,p,t)
end
```
