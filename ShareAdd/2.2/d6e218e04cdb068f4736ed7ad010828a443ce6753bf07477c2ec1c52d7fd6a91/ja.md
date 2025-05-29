```
mutable struct PackageInfo
```

  * `name::String` - パッケージの名前
  * `envs::Vector{EnvInfo}` - パッケージが存在する環境のリスト
  * `in_path::Bool` - 環境のいずれかが `LOAD_PATH` にあるかどうか

この型は公開されており、エクスポートされていません。
