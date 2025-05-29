```
@ode_def name begin
    微分方程
end parameters :: ODEFunction
```

## ドメイン特化型言語 (DSL) の定義

ヘルパーマクロが提供されており、`ParameterizedFunction` を定義するのが容易になります。また、微分方程式ソルバーをより速く実行するために、いくつかの追加関数を象徴的に計算します。たとえば、前の `LotkaVolterra` を定義するには、次のコマンドを使用できます。

```julia
f = @ode_def LotkaVolterra begin
    dx = a * x - b * x * y
    dy = -c * y + d * x * y
end a b c d
```

または、匿名で定義することもできます。

```julia
f = @ode_def begin
    dx = a * x - b * x * y
    dy = -c * y + d * x * y
end a b c d
```

`@ode_def` は内部で ModelingToolkit.jl を使用し、MTK の象徴的ツールを通じて定義された追加の定義（ヤコビ行列、パラメータヤコビ行列など）を持つ `ODEFunction` を返します。
