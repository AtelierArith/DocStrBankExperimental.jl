```
delete_index(ctx::PineconeContext, indexobj::PineconeIndex)
```

インデックスを削除し、Pineconeバックエンドからの成功レスポンスに対してtrueを返します。

指定されたPineconeインデックスを削除します。この呼び出しは非同期であり、戻り値がインデックスが実際に削除されたことを保証するものではありません（まだ削除されていない可能性があります）。

# 例

```julia
Pinecone.delete_index(context, Pinecone.Index("index-to-delete"))
```
