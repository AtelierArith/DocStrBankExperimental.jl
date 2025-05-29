```
dynamicfiles(folder::String, mountdir::String; headers::Vector{Pair{String,String}}=[], loadfile::Union{Function,Nothing}=nothing)
```

/staticフォルダー内のすべてのファイル（またはユーザー定義のマウントポイント）をマウントしますが、ファイルは各リクエストごとに再読み込みされます。`headers`配列はすべてのマウントされたファイルに適用されます。
