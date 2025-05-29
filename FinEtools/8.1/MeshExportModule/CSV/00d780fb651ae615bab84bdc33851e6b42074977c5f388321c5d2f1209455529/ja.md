```
savecsv(name::String; kwargs...)
```

配列をCSVファイルとして保存します。

例:

```julia
savecsv("ab", a = rand(3), b = rand(3))
```
