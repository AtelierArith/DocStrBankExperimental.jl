```
GitHubRepo(url::String; paths = ["src", "docs/src", "README.md"],
    file_types = [".jl", ".md"])
```

ターゲットGitHubリポジトリを表す`GitHubRepo`オブジェクトを作成します。

# 引数

  * `url::String`: GitHubリポジトリのURL。
  * `paths::Vector{String}`: スキャンするフォルダとファイル。
  * `file_types::Vector{String}`: スキャンで受け入れるファイルタイプ。

# フィールド

  * `owner::String`: リポジトリの所有者。
  * `name::String`: リポジトリの名前。
  * `url::String`: リポジトリのURL。
  * `paths::Vector{String}`: スキャンするフォルダとファイル。
  * `file_types::Vector{String}`: スキャンで受け入れるファイルタイプ。

注意: ファイルとフォルダは再帰的にスキャンされます。

主なメソッド: `scan_github_path`, `create_cheatsheet`, `collect`.

  * `scan_github_path`はリポジトリをスキャンし、すべての関連ファイルのリストを取得するために使用されます。
  * `create_cheatsheet`はリポジトリからチートシートを作成するために使用されます。
  * `collect`はリポジトリの内容を単一の文字列にまとめるために使用されます（要約なし）。

# 例

```julia
repo = GitHubRepo("https://github.com/username/repository")
files = scan_github_path(repo)
```

チートシートを作成し、自動的にファイルに保存しましょう：

```julia
repo = GitHubRepo("https://github.com/username/repository")
cheatsheet = create_cheatsheet(repo; save_path = true)
```

リポジトリ内のすべてのファイルを収集しましょう（例：LLM呼び出し用）：

```julia
repo = GitHubRepo("https://github.com/username/repository")
collated = collect(repo)
```
