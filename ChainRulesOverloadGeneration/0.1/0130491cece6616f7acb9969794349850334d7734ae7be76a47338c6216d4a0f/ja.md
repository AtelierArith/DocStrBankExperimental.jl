```
refresh_rules()
refresh_rules(frule | rrule)
```

これにより、すべての [`on_new_rule`](@ref) フックが新しく定義されたルールに対して実行されます。これは、パッケージが読み込まれるたびに *自動的に* 実行されます。また、REPLでルールが定義された場合やAD関数と同じファイル内で定義された場合など、直接実行するために手動で呼び出すこともできます。
