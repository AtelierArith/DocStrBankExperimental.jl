```
generate(dst_path[, data]; kwargs...)
generate(src_path, dst_path[, data]; true, kwargs...)
```

テンプレートを使用して、`dst_path` に新しいプロジェクトを生成します。`dst_path` がすでに存在する場合、これはエラーをスローしますが、`dst_path = "."` の場合は除きます。既存のパッケージには、代わりに `BestieTemplate.apply` を使用してください。

BestieTemplate テンプレートを使用して、[copier](https://github.com/copier-org/copier) の `copy` コマンドを実行します。`src_path` が指定されていない場合、BestieTemplate.jl の GitHub URL が使用されます。

`data` 引数は、インタラクティブな質問の一部をバイパスするために使用できる質問（キー）に対する回答（値）の辞書です。

## キーワード引数

  * `warn_existing_pkg::Boolean = true`: 実際に `update` を意味しているかどうかを確認するかどうか。`generate` を実行し、`dst_path` に `.copier-answers.yml` が含まれている場合、コピーはすでに行われたことを意味するため、代わりに `update` を意味している可能性があります。`true` の場合、警告が表示され、実行が停止します。
  * `quiet::Boolean = false`: 挨拶、情報、その他のメッセージを表示するかどうか。このキーワードは copier にも使用されます。

他のキーワード引数は、内部の [`Copier.copy`](@ref) に直接渡されます。
