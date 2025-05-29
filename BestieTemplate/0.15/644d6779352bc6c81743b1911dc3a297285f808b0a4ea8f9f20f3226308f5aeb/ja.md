```
apply(dst_path[, data]; kwargs...)
apply(src_path, dst_path[, data]; true, kwargs...)
```

$$
dst_path
$$

にある既存のプロジェクトにテンプレートを適用します。`dst_path` が存在しない場合、エラーが発生します。新しいパッケージの場合は、代わりに `BestieTemplate.generate` を使用してください。

BestieTemplate テンプレートを使用して [copier](https://github.com/copier-org/copier) の `copy` コマンドを実行します。`src_path` が指定されていない場合、BestieTemplate.jl の GitHub URL が使用されます。

`data` 引数は、インタラクティブな質問の一部をバイパスするために使用できる質問（キー）への回答（値）の辞書です。

## キーワード引数

  * `guess:Bool = true`: パッケージ自体からデータを推測しようとするかどうか。
  * `warn_existing_pkg::Bool = true`: 実際に `update` を意味しているかどうかを確認するかどうか。`apply` を実行し、`dst_path` に `.copier-answers.yml` が含まれている場合、コピーはすでに行われていることを意味するため、代わりに `update` を意味している可能性があります。`true` の場合、警告が表示され、実行が停止します。
  * `quiet::Bool = false`: 挨拶、情報、その他のメッセージを表示するかどうか。このキーワードは copier にも使用されます。

他のキーワード引数は、内部の [`Copier.copy`](@ref) に直接渡されます。
