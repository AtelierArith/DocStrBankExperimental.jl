```
xkb_state_match
```

[`xkb_state_mod_indices_are_active`](@ref)() および [`xkb_state_mod_names_are_active`](@ref)() のためのマッチフラグで、成功するマッチの条件を指定します。XKB*STATE*MATCH*NON*EXCLUSIVE は他のモードとビットマスク可能です。

| 列挙子                           | 注釈                                                      |
|:----------------------------- |:------------------------------------------------------- |
| XKB*STATE*MATCH_ANY           | いずれかの修飾子がアクティブであれば true を返します。                          |
| XKB*STATE*MATCH_ALL           | すべての修飾子がアクティブであれば true を返します。                           |
| XKB*STATE*MATCH*NON*EXCLUSIVE | マッチを非排他的にし、引数に指定されていない修飾子がアクティブであっても false を返さないようにします。 |
