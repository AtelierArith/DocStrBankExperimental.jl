```
struct GitHubProject
    owner::String
    package::String
    branch::String
    basedir::String
end
```

この構造体は、私たちが情報をダウンロードするGitHubプロジェクトの詳細を保持します。

**値:**

| 名前      | 説明                       |
|:------- |:------------------------ |
| owner   | プロジェクトの所有者。              |
| package | 探索するパッケージ。               |
| branch  | 使用するブランチ。                |
| basedir | ファイルを探すためのパッケージ内のディレクトリ。 |
