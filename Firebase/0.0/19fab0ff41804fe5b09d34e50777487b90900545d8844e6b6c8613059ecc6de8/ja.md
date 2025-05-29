get_request(url::String)

# 一般的な性質のGETリクエストで、任意のドキュメントまたはコレクションを取得します

# 例

```julia
init("[FIREBASE_ADMIN_SDK].json")
res = get_request("/firebase_test/firebase_get") # ドキュメント取得
res = get_request("/firebase_test/firebase_get/firebase_get_collection") # コレクション取得
```
