```
bea_datasets(;user_id::String = USER_ID) -> DataFrame
```

BEAデータAPIを通じてアクセス可能なデータセットの名前と説明の`DataFrame`を返します。

例:

```julia
# ユーザーIDは ~/.beadatarc に保存されています
julia> bea_datsets();

julia> show(ans[1:3, :])
3×2 DataFrames.DataFrame
│ Row │ DatasetName        │ Description                          │
│     │ String             │ String                               │
├─────┼────────────────────┼──────────────────────────────────────┤
│ 1   │ NIPA               │ 標準NIPAテーブル                     │
│ 2   │ NIUnderlyingDetail │ 標準NI基礎詳細テーブル               │
│ 3   │ MNE                │ 多国籍企業                           │
```
