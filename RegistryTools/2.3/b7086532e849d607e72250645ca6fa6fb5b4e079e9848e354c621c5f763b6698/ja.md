```
register(package_repo, pkg, tree_hash; registry, registry_fork, registry_deps, push, gitconfig)
```

`registry`において`package_repo` / `tree_hash`でパッケージを登録します。登録に関する情報や発生したエラーまたは警告を含む`RegEdit.RegBranch`を返します。

# 引数

  * `package_repo::AbstractString`: 登録するパッケージのためのgitリポジトリのURL。空の場合は、保存されたリポジトリのURLを保持します。
  * `pkg::String`: 登録するパッケージのプロジェクトファイルのパス
  * `tree_hash::AbstractString`: 登録するパッケージのリビジョンのツリーハッシュ（コミットハッシュではない）

# キーワード引数

  * `registry::AbstractString="https://github.com/JuliaRegistries/General"`: レジストリのためのgitリポジトリのURL
  * `registry_fork::AbstractString=registry`: レジストリのフォークのためのgitリポジトリのURL
  * `registry_deps::Vector{String}=[]`: `pkg`に依存するパッケージを含む任意のレジストリのgitリポジトリのURL
  * `subdir::AbstractString=""`: `package_repo`内のパッケージへのパス
  * `push::Bool=false`: 登録ブランチを`registry`にプッシュして考慮するかどうか
  * `gitconfig::Dict=Dict()`: `git`コマンドのための設定オプションの辞書
