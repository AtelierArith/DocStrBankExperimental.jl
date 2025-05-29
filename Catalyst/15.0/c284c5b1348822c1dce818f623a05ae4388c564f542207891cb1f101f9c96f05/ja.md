getdescription(reaction::Reaction)

入力反応の`description`メタデータフィールドを返します。

引数:

  * `reaction`: `description`メタデータフィールドを取得したい反応。

例:

```julia
reaction = @reaction k, 0 --> X, [description="A reaction"]
getdescription(reaction)
```
