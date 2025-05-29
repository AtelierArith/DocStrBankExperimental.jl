firestore_commit(transactionid="",body =body)

Commits a transaction, while optionally updating documents.

# Example

```julia
init("[FIREBASE_ADMIN_SDK].json")
data = firestore_beginTransaction()
firestore_commit(data["transaction"])
```
