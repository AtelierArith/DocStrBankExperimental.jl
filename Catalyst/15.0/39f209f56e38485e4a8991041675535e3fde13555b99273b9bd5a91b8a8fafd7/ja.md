```
SymbolicUtils.getmetadata(reaction::Reaction, md_key::Symbol)
```

`Reaction`から特定のメタデータ値を取得します。メタデータが存在しない場合は、エラーをスローします。

引数:

  * `reaction`: 特定のメタデータ値を取得したい反応。
  * `md_key`: 取得したいメタデータ。

例:

```julia
reaction = @reaction k, 0 --> X, [description="Production reaction"]
getmetadata(reaction, :description)
```
