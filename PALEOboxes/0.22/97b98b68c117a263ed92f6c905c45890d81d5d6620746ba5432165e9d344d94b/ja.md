```
create_reaction(rdict::Dict{String, Type}, classname::String, name::String, external_parameters::Dict{String, Any}) -> reaction::AbstractReaction
create_reaction(ReactionType::Type{<:AbstractReaction}, name::String, external_parameters::Dict{String, Any}) -> reaction::AbstractReaction
```

反応を作成して構成します。

`ReactionBase`を名前、クラス名、外部パラメータで設定します。
