```
set_taped_globals!(t::TapedTask, new_taped_globals)::Nothing
```

`t` の `taped_globals` を `new_taped_globals` に設定します。今後の `consume(t)` への呼び出し（直接的に、または反復を介して暗黙的に）での [`get_taped_globals`](@ref) への呼び出しは、この新しい値を参照します。
