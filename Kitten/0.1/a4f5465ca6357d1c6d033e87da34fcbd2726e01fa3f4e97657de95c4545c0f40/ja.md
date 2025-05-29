```
@dynamicfiles(folder::String, mountdir::String, headers::Vector{Pair{String,String}}=[])
```

/staticフォルダ内のすべてのファイル（またはユーザー定義のマウントポイント）をマウントしますが、ファイルは各リクエストごとに再読み込みされます。
