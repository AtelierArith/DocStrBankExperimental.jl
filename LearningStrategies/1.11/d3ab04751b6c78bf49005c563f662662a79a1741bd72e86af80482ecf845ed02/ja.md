```
learn!(model, strategy, data) -> model
```

`data`を使用して`strategy`から`model`を学習します。新しいモデル/戦略/データ型は、少なくとも次のいずれかをオーバーロードする必要があります。

  * [`setup!`](@ref)
  * [`update!`](@ref)
  * [`hook`](@ref)
  * [`finished`](@ref)
  * [`cleanup!`](@ref)

# `learn!` 実装:

```
function learn!(model, s::LearningStrategy, data)
    setup!(s, model[, data])
    for (i, item) in enumerate(data)
        update!(model, s[, i], item)
        hook(s, model[, data], i)
        finished(s, model[, data], i) && break
    end
    cleanup!(s, model)
end
```
