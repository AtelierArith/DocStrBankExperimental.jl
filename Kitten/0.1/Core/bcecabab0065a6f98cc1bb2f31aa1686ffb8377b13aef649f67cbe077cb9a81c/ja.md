```
staticfiles(folder::String, mountdir::String; headers::Vector{Pair{String,String}}=[], loadfile::Union{Function,Nothing}=nothing)
```

/staticフォルダー内のすべてのファイル（またはユーザー定義のマウントポイント）をマウントします。`headers`配列は、すべてのマウントされたファイルに適用されます。
