firestore_batchget(batch=body)

複数のドキュメントを取得します。このメソッドによって返されるドキュメントは、要求されたのと同じ順序で返されることは保証されていません。

# 例

```julia
init("[FIREBASE_ADMIN_SDK].json")
res = firestore_batchget()
```
