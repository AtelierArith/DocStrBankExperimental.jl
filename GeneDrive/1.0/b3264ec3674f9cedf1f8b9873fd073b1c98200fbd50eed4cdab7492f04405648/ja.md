```
get_previous_lifestage(node::Node, species::Type{<:Species}, ::Stage{T}) where T <: LifeStage
```

`LifeStage`の依存関係を示します：`Node`内の`Species`の指定された`LifeStage`の前の`LifeStage`のデータを返します。
