```
SymbolicUtils.hasmetadata(reaction::Reaction, md_key::Symbol)
```

特定のメタデータフィールドを持つかどうかを`Reaction`でチェックします。もし持っていれば`true`を返し（そうでなければ`false`を返します）。

引数:

  * `reaction`: 特定のメタデータフィールドが存在するかどうかを確認したい反応。
  * `md_key`: 存在を確認したいメタデータ。

例:

```julia
reaction = @reaction k, 0 --> X, [description="Production reaction"]
hasmetadata(reaction, :description)
```
