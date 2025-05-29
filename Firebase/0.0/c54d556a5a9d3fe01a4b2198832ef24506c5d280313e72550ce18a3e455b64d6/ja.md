firestore_deletedoc(url)

ドキュメントを削除します

# 例

```julia
init("[FIREBASE_ADMIN_SDK].json")
firestore_createdoc("/firebase_test/firebase_post/three";query ="hello") # ドキュメントを作成し、その後削除します
firestore_deletedoc("/firebase_test/firebase_post/three/hello")
```
