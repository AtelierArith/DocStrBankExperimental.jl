```
unfreeze!(@nospecialize(ids::T), field::Symbol) where {T<:IDS}
```

もしidsフィールドに関連付けられた式があり、それが凍結されている場合、それを再び式に戻します。
