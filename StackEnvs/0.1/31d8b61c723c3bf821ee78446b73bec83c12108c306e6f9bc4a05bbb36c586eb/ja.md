```
is_in_stack(env_name::AbstractString)::Bool
```

共有環境 `env_name` が環境スタックにある場合は `true` を返します。

`env_name` が `'@'` で始まらない場合は、先頭に追加されます。スタックは `Base.LOAD_PATH` です。
