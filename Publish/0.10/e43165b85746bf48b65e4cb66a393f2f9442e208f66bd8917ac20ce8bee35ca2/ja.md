```
setup(dir)
```

指定されたディレクトリ `dir` に `Publish` プロジェクトを初期化します。ディレクトリが存在しない場合は作成されます。

`dir` に `Project.toml` ファイルを持つ Julia プロジェクト構造がある場合、`Publish` はその依存関係リストに追加されます。それ以外の場合、Julia パッケージでない場合は、`Project.toml` ファイルと `README.md` ファイルが作成されます。

## キーワード

  * `pkg::Bool=true` は、`setup` の使用中にすべての `Pkg` 呼び出しを無効にするために `false` に設定できます。
