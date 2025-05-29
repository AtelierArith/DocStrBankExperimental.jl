```
fits_write_key(f::FITSFile, keyname::String, value, comment::Union{String, Nothing} = nothing)
```

適切なデータ型のキーワードをCHUに書き込みます。`comment`が`nothing`の場合、コメントなしでキーワードが書き込まれます。
