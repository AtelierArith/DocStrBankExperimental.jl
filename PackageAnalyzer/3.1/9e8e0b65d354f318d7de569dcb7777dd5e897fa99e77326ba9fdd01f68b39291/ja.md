```
analyze(name_or_dir_or_url::AbstractString; registry=general_registry(), auth::GitHub.Authorization=github_auth(), version=nothing)
```

必須引数で指し示されたパッケージを分析し、そのプロパティの概要を返します。

  * `name_or_dir_or_url` が有効なJulia識別子である場合、それは `registry` で利用可能なパッケージの名前であると見なされます。この関数は [`find_package`](@ref) を使用してレジストリ内のエントリを見つけ、最新の登録バージョンの内容を分析します（または、キーワード引数 `version` が指定されている場合は別のバージョンを分析します）。
  * `name_or_dir_or_url` がファイルシステムのパスである場合、`name_or_dir_or_url` にあるソースコードのパッケージを分析します。
  * それ以外の場合、`name_or_dir_or_url` はURLであると見なされます。リポジトリは一時ディレクトリにクローンされ、分析されます。

GitHubの認証が匿名でなく、リポジトリがGitHub上にある場合、リポジトリへの貢献者のリストも収集されます。概要には貢献者の数のみが表示されます。GitHub認証を取得するには [`PackageAnalyzer.github_auth`](@ref) を参照してください。

!!! warning
    サブディレクトリ内のパッケージについては、トップレベルの情報（CIスクリプトなど）は、`name_or_dir_or_url` がURLである場合、または `name_or_dir_or_url` が名前で `version = :dev` である場合にのみ利用可能です。それ以外の場合、トップレベルのコードにはアクセスできません。


## 例

パッケージをその名前だけで分析できます。ローカルにインストールされているかどうかは関係ありません：

```julia
julia> analyze("Pluto"; version=v"0.18.0")
PackageV1 Pluto:
  * repo: https://github.com/fonsp/Pluto.jl.git
  * uuid: c3e4b0f8-55cb-11ea-2926-15256bba5781
  * version: 0.18.0
  * is reachable: true
  * tree hash: db1306745717d127037c5697436b04cfb9d7b3dd
  * Julia code in `src`: 8337 lines
  * Julia code in `test`: 5448 lines (39.5% of `test` + `src`)
  * documention in `docs`: 0 lines (0.0% of `docs` + `src`)
  * documention in README: 118 lines
  * has license(s) in file: MIT
    * filename: LICENSE
    * OSI approved: true
  * has license(s) in Project.toml: MIT
    * OSI approved: true
  * has `docs/make.jl`: false
  * has `test/runtests.jl`: true
  * has continuous integration: true
    * GitHub Actions

```
