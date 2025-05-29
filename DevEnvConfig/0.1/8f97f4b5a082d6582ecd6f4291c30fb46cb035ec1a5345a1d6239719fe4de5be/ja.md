```
function newpkg(pkname::String;
    dir             :: String|∅ = nothing,
    docrepo         :: String|∅ = nothing,
    private         :: Bool     = false,
    useextjl        :: Bool|∅   = nothing,
    generalregistry :: Bool|∅   = nothing,
    license         :: String|∅ = nothing) -> ActionStatus
```

新しいパッケージを作成します。これにより、あなたのGitHubアカウントを使用して:

  * ドキュメント生成とデプロイの設定、
  * ユニットテストとバッジステータスの設定、
  * CodeCovでのコードカバレッジとバッジステータスの設定

このテンプレートは、プライベートパッケージリポジトリを処理し、別の（公開）リポジトリでのドキュメントデプロイを行います。また、プライベートリポジトリのコードカバレッジレポートのためのガイド付きセットアップも提供します。

# 引数

  * `pkname`: 新しいJuliaパッケージの名前
  * `dir`: パッケージを作成するディレクトリ、デフォルトは`JULIA_PKG_DEVDIR`
  * `docrepo`: ドキュメントを公開するために使用されるGitHubリポジトリの名前、デフォルトはパッケージリポジトリ。
  * `private`: このパッケージがプライベートGitHubリポジトリにホストされている場合は`true`に設定
  * `useextjl`: GitHubリポジトリが`PackageName.jl`と名付けられている場合は`true`に設定、デフォルトは`!private`
  * `generalregistry`: このパッケージが一般に登録される場合は`true`に設定、デフォルトは`!private`
  * `license`: LICENSEファイルの名前、公開パッケージの場合はデフォルトで`MIT`
