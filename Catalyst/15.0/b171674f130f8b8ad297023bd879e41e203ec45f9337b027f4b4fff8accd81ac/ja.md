hasdescription(reaction::Reaction)

入力反応に`description`メタデータフィールドが割り当てられている場合は`true`を返し、そうでない場合は`false`を返します。

引数:

  * `reaction`: `description`メタデータフィールドをチェックしたい反応。

例:

```julia
reaction = @reaction k, 0 --> X, [description="A reaction"]
hasdescription(reaction)
```
