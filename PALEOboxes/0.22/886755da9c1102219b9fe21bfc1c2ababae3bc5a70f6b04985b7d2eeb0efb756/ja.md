```
create_reaction(ReactionType::Type{<:AbstractReaction}, base::ReactionBase) -> reaction::AbstractReaction
```

`ReactionType`を作成し、`base`フィールドを設定するためのデフォルトメソッドです。

反応の実装は、追加のフィールドを設定するためにカスタムメソッドをオプションで実装することができます。
