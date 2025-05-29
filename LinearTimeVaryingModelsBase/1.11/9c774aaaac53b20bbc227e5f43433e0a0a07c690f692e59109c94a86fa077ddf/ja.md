モデルインターフェース、次の関数を実装します

`AbstractCost`、`ModelAndCost`も参照してください。

```
fit_model(::Type{AbstractModel}, batch::Batch)::AbstractModel

predict(model::AbstractModel, x, u)

function df(model::AbstractModel, x, u, I::UnitRange)
    return fx,fu,fxx,fxu,fuu
end
```
