```
scan_github_path(repo::GitHubRepo, path::String; verbose = true,
    http_kwargs::NamedTuple = NamedTuple())

scan_github_path(repo::GitHubRepo; verbose = true,
    http_kwargs::NamedTuple = NamedTuple())
```

特定のGitHubリポジトリ内のパスをスキャンし、`repo`の基準を満たすファイルのリストを返します。ネストされたフォルダも再帰的にスキャンします。

注意: GitHubによってレート制限を受けている場合は、`ENV["GITHUB_API_KEY"]`にAPIキーを設定してください。

# 引数

  * `repo::GitHubRepo`: スキャンするリポジトリ。
  * `path::String`: リポジトリ内でスキャンするパス。パスが提供されていない場合、リポジトリオブジェクト内のすべてのパスをスキャンします。
  * `verbose::Bool`: 詳細な出力を表示するかどうか。
  * `http_kwargs::NamedTuple`: `github_api`に渡す追加のキーワード引数。

# 戻り値

  * `Vector{JSON3.Object}`: 指定されたパス内のファイルとフォルダのリスト。
