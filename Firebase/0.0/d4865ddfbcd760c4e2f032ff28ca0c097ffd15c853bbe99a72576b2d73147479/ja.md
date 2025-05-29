firebase*deleteuser(firebase*id*token=FIREBASE*ID_TOKEN)

アカウントの削除 現在のユーザーは、Auth deleteAccount エンドポイントに HTTP POST リクエストを発行することで削除できます。

# 例

```julia
data = firebase_signup("ashwani121231@gmail.com","hello!!123")
firebase_deleteuser(data["idToken"])
```
