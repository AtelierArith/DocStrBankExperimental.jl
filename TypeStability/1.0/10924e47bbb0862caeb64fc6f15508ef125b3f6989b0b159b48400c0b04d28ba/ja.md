```
enable_inline_stability_checks(::Bool)
```

[`@stable_function`](@ref)からインライン安定性チェックを実行するかどうかを設定します。

`false`（デフォルト値）に設定されている場合、@stable_functionは型の安定性チェックを実行しません。

値は@stable_functionが評価されるときにチェックされるため、通常はパッケージ定義の最初に設定する必要があります。

[`inline_stability_checks_enabled`](@ref)を参照してください。
