```
info(name::String; pkg=nothing, interactive=false)
```

指定された `name` を持つ登録されたモデルタイプのメタデータを返します。重複する名前の場合、キーワード引数 `pkg` が必要ですが、代わりに `interactive=true` が指定されている場合は必要ありません。

代わりにモデルのドキュメント文字列を返すには（定義コードをインポートせずに） `doc(name; pkg=...)` を実行してください。

参照してください [`doc`](@ref).
