```
env_exists(env_name::AbstractString)::Bool
```

共有環境 `env_name` がすでに存在する場合は `true` を返します。

`env_name` は "@" で始まる場合もありますし、そうでない場合もあります。

この環境は `Pkg.activate(env_name)` を介してアクティブ化できます。`pkg` repl から行う場合、名前は `'@'` で始まる必要があります。
