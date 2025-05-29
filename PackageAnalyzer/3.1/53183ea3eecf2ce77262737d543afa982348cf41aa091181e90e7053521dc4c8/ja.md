```
analyze_packages(pkg_entries; auth::GitHub.Authorization=github_auth(), sleep=0, root=mktempdir()) -> Vector{PackageV1}
```

イテラブル `pkg_entries` 内のすべてのパッケージを分析し、必要に応じてそのコードを `root` に保存します。 `Vector{PackageV1}` を返します。

`pkg_entries` の各要素は [`analyze`](@ref) に対する有効な入力である必要があります。

GitHub 認証が匿名でなく、リポジトリが GitHub にある場合、リポジトリの貢献者のリストも収集されます。各エントリのために `sleep` 秒待った後に行われます（GitHub によるレート制限を回避するのに役立ちます）。 GitHub 認証を取得するには [`PackageAnalyzer.github_auth`](@ref) を参照してください。
