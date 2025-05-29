```
create_reaction(ReactionType::Type{<:AbstractReaction}, base::ReactionBase) -> reaction::AbstractReaction
```

Default method to create a `ReactionType` and set `base` field.

A reaction implementation may optionally implement a custom method eg to set additional fields
