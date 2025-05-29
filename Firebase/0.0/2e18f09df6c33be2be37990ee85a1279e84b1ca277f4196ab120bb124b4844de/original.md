firestore_createdoc(url, body)

# Example

```julia
init("[FIREBASE_ADMIN_SDK].json")
firestore_createdoc("/firebase_test/firebase_post/two") 
firestore_createdoc("/firebase_test/firebase_post/three";query ="hello") # with document id name in query
```
