```
FilesDaf(
    path::AbstractString,
    mode::AbstractString = "r";
    [name::Maybe{AbstractString} = nothing]
)
```

ディスクファイルのストレージは、特定のディレクトリにあります。

既存のデータセットを開くとき、`name`が指定されていない場合、"name"スカラープロパティが存在すればそれが名前として使用されます。そうでなければ、`path`が名前として使用されます。

有効な`mode`の値は以下の通りです（デフォルトモードは`r`です）：

| モード  | 修正を許可しますか？ | 存在しない場合に作成しますか？ | 存在する場合に切り詰めますか？ | 戻り値の型                 |
|:---- |:---------- |:--------------- |:--------------- |:--------------------- |
| `r`  | いいえ        | いいえ             | いいえ             | [`DafReadOnly`](@ref) |
| `r+` | はい         | いいえ             | いいえ             | [`FilesDaf`](@ref)    |
| `w+` | はい         | はい              | いいえ             | [`FilesDaf`](@ref)    |
| `w`  | はい         | はい              | はい              | [`FilesDaf`](@ref)    |
