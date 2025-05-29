```
refreeze!(@nospecialize(ids::T), field::Symbol, @nospecialize(default::Any=missing)) where {T<:IDS}
```

もしidsフィールドに関連付けられた式がある場合、それをその場で再評価します。

式が失敗した場合、デフォルト値が割り当てられます。
