```
mutable struct EnvInfo
EnvInfo(name::AbstractString) -> EnvInfo
```

  * `name::String` - 環境の名前
  * `path::String` - 環境のフォルダのパス
  * `pkgs::Set{String}` - 環境内のパッケージのリスト
  * `in_path::Bool` - 環境が `LOAD_PATH` にあるかどうか
  * `standard_env::Bool = false` - 環境が標準のものであるかどうか（Julia v1.11 の `v1.11` フォルダにある）
  * `shared::Bool = true` - 共有環境であるかどうか
  * `temporary::Bool = false` - 一時的な環境であるかどうか
  * `active_project::Bool = false` - アクティブなプロジェクトであるかどうか

# 例

```julia-repl
julia> ShareAdd.EnvInfo("@DocumenterTools")
ShareAdd.EnvInfo("DocumenterTools", "/Users/eben60/.julia/environments/DocumenterTools", Set(["DocumenterTools"]), false, false, true, false, false)
```

この型は公開されており、エクスポートされていません。
