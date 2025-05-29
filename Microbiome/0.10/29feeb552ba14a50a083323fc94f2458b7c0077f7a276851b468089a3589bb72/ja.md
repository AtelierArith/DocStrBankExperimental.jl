```
set!(cp::CommunityProfile, md; namecol=:sample)
```

`CommunityProfile`にメタデータ（`Tables.jl`テーブルの形式で）を追加します。1つの列（`namecol`）には`commp`に存在するサンプル名が含まれ、他の列には各サンプルのメタデータが追加されます。
