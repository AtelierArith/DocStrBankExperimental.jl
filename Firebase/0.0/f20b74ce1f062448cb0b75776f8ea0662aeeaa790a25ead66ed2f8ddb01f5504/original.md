firestore_batchget(batch=body)

Gets multiple documents Documents returned by this method are not guaranteed  to be returned in the same order that they were requested.

# Example

```julia
init("[FIREBASE_ADMIN_SDK].json")
res = firestore_batchget()
```
