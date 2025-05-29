```julia
struct Repo
```

データ構造はgitリポジトリを表します。これはローカルファイルシステム上の特定のパスに関連付けられているため、パスが削除されると無効になります。

## 例

```julia
r = Repo("/path/to/repo")  # 既存のリポジトリ
r = clone("https://path/to/repo.git", "newrepo")  # リモートからクローンし、リポジトリを返す

r = Repo("/phat/to/NOT/repo")  # validate=falseでない限り、非リポジトリではエラーになります

mkdir("newnewrepo")
r = init("newnewrepo")  # 新しいgitリポジトリを作成
```
