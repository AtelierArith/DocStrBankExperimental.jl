```
Git(;
    ignore=String[],
    name=nothing,
    email=nothing,
    branch=LibGit2.getconfig("init.defaultBranch", "main")
    ssh=false,
    jl=true,
    manifest=false,
    gpgsign=false,
)
```

Gitリポジトリと`.gitignore`ファイルを作成します。

## キーワード引数

  * `ignore::Vector{<:AbstractString}`: `.gitignore`に追加するパターン。詳細は[`gitignore`](@ref)を参照してください。
  * `name::AbstractString`: Gitで`user.name`を設定していない場合のあなたの本名。
  * `email::AbstractString`: Gitで`user.email`を設定していない場合のあなたのメールアドレス。
  * `branch::AbstractString`: リポジトリのデフォルトブランチの希望する名前。
  * `ssh::Bool`: リモートにSSHを使用するかどうか。未設定の場合はHTTPSが使用されます。
  * `jl::Bool`: リモートURLに`.jl`サフィックスを追加するかどうか。
  * `manifest::Bool`: `Manifest.toml`をコミットするかどうか。
  * `gpgsign::Bool`: コミットをGPGキーで署名するかどうか。このオプションはGit CLIがインストールされていることと、コミッターのアイデンティティに関連付けられたGPGキーが必要です。
