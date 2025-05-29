```
stringify(var::Union{String,Symbol}, n::Integer)
```

文字列またはシンボルを次のように文字列化します：

  * `n >= 0` の場合は `_var__n_` を返します
  * `n < 0` の場合は `_var_mn_` を返します
