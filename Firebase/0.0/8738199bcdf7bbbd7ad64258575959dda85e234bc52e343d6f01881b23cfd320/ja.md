firebase*getuserinfo(firebase*id*token=FIREBASE*ID_TOKEN)

ユーザーデータを取得するには、Auth getAccountInfoエンドポイントにHTTP POSTリクエストを発行します。

# 例

```julia
data = firebase_signin("ab669522@gmail.com","helloworld!!")
firebase_getuserinfo(data["idToken"])
```
