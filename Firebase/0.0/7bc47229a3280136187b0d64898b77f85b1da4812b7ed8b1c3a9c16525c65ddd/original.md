firestore_batchwrite(batch=body)

Applies a batch of write operations. The documents.batchWrite method does not apply the write operations atomically and can apply them out of order. Method does not allow more than one write per document.  Each write succeeds or fails independently. See the BatchWriteResponse for the success  status of each write.

If you require an atomically applied set of writes, use documents.commit instead.

# Example

```julia
init("[FIREBASE_ADMIN_SDK].json")
res = firestore_batchwrite()
```
