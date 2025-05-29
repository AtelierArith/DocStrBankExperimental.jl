```
refit!(m::GeneralizedLinearMixedModel[, y::Vector];
       fast::Bool = (length(m.θ) == length(m.optsum.final)),
       nAGQ::Integer = m.optsum.nAGQ,
       kwargs...)
```

モデル `m` を応答 `y` をインストールした後に再フィットします。

`y` が省略された場合、現在の応答ベクトルが使用されます。

指定されていない場合、前のフィットからの `fast` および `nAGQ` オプションが使用されます。 `kwargs` は [`fit!`](@ref) と同じです。
