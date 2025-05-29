get_revision(rtype::Type{RT}, cid::DbId, vid::DbId) where {RT<:ComponentRevision}

```
cidのコンポーネントのvidのバージョンとしてのリビジョンを取得します
リビジョンは存在しなければなりません
```
