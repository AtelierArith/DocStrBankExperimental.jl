```
process_folder(folder="src") -> Vector{FileCoverage}
```

Juliaソースコードのフォルダーの内容を処理して、含まれているすべてのファイルのカバレッジ統計を収集します。子フォルダーを再帰的にトラバースします。デフォルトのフォルダーは「src」で、これはCoverageToolsがパッケージのルートディレクトリから呼び出される主要なケースに便利です。
