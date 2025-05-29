```
test_patterns(patterns::Vector{Union{String,Regex}})::Nothing
```

テストを実行するためのパターンを指定します。`test_name` の完全な一致がパターンのいずれかにマッチするテストのみが実行されます。ベクターが空の場合、すべてのテストが実行されます。
