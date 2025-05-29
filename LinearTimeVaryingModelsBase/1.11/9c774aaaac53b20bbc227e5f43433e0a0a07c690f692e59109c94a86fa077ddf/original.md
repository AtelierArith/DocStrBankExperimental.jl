Model interface, implement the following functions

see also `AbstractCost`, `ModelAndCost`

```
fit_model(::Type{AbstractModel}, batch::Batch)::AbstractModel

predict(model::AbstractModel, x, u)

function df(model::AbstractModel, x, u, I::UnitRange)
    return fx,fu,fxx,fxu,fuu
end
```
