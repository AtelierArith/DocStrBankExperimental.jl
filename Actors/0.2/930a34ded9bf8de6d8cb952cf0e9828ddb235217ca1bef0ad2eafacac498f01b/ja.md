```
term!(lk::Link, f, args1...; kwargs...)
term!(name::Symbol, ....)
```

アクター `lk`（または登録されている場合は `name::Symbol`）に、与えられた部分引数と終了時の理由で `f` を実行するよう指示します。

終了理由は、アクターが終了する際に `args1...` に追加されます。
