firestore_createdoc(url, body)

# 例

```julia
init("[FIREBASE_ADMIN_SDK].json")
firestore_createdoc("/firebase_test/firebase_post/two") 
firestore_createdoc("/firebase_test/firebase_post/three";query ="hello") # クエリ内のドキュメントID名
```
