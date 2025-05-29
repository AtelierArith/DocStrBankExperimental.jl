```
require_file(f::Function, file::Union{String, Array{String}})
```

`file`内のファイル/リンク/ディレクトリのいずれかが存在しない場合、`f`を実行します。
