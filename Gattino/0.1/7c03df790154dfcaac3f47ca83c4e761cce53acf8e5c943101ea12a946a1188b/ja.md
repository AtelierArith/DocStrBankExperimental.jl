```julia
open_layer!(f::Function, con::AbstractContext, layer::String) -> ::Nothing
```

`open_layer` は `con` から `layer` を開き、そのレイヤー内の各 `Component` をその列挙と共に `f` に提供します。これにより、`set!`、`set_gradient!`、および追加の `style!` ディスパッチを使用して、全体のレイヤーに変更を加えることができます。いくつかのディスパッチでは、これらのレイヤーはデータに基づいており、さらに特徴を表現することができます。

```example

```
