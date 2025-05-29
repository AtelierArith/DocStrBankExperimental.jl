```
SkipFromAdmin(admin::AbstractString, idxs::AbstractVector{<:Integer})
SkipFromAdmin(admin::AbstractString, idx::Int)
SkipFromAdmin(admin::AbstractString, [::Colon])
```

国境を生成する際にスキップする国の部分を指定するために使用される構造体 [`extract_countries`](@ref) と共に。

国名または国名と `Colon` (`:`) のインスタンスのみでインスタンス化された場合、`admin` で始まる ADMIN 名の完全な国が `extract_countries` の出力から削除されることを示します（大文字と小文字を区別）。

`admin` 名と整数インデックスのリストで作成された場合、提供されたインデックスのポリゴンは、`extract_countries` の出力に `admin` が存在する場合、その国に関連付けられた `MultiPolyArea` から削除されます。

## 注意

コンストラクタは、提供された `admin` が存在するか、提供された `idxs` が `admin` の境界に関連付けられた `MultiPolyArea` にインデックスを付けるのに有効であるかを検証するための検証を行いません。
