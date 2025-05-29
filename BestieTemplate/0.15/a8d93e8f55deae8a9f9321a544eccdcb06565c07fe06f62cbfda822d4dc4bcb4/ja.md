```
update([data]; kwargs...)
update(dst_path[, data]; kwargs...)
```

copierのupdateコマンドを実行し、`dst_path`（省略した場合は現在のパス）を新しいバージョンのテンプレートで更新します。

`data`引数は、インタラクティブな質問の一部をバイパスするために使用できる質問（キー）への回答（値）の辞書です。

## キーワード引数

キーワード引数は、内部の[`Copier.update`](@ref)に直接渡されます。
