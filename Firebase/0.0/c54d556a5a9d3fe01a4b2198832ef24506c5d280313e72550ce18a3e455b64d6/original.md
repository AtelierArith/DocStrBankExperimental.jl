firestore_deletedoc(url)

Deletes a document

# Example

```julia
init("[FIREBASE_ADMIN_SDK].json")
firestore_createdoc("/firebase_test/firebase_post/three";query ="hello") # creates the document and then we delete it
firestore_deletedoc("/firebase_test/firebase_post/three/hello")
```
