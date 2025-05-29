firestore_batchwrite(batch=body)

一連の書き込み操作を適用します。documents.batchWriteメソッドは、書き込み操作を原子的に適用せず、順不同で適用することがあります。このメソッドは、ドキュメントごとに1つの書き込みしか許可しません。各書き込みは独立して成功または失敗します。各書き込みの成功ステータスについては、BatchWriteResponseを参照してください。

原子的に適用された書き込みのセットが必要な場合は、documents.commitを使用してください。

# 例

```julia
init("[FIREBASE_ADMIN_SDK].json")
res = firestore_batchwrite()
```
