firebase*verifyemail(firebase*id*token=FIREBASE*ID_TOKEN)

メール確認を送信 現在のユーザーに対してメール確認を送信するには、Auth getOobConfirmationCodeエンドポイントにHTTP POSTリクエストを発行します。

# 例

```julia
data = firebase_signin("ab669522@gmail.com","helloworld!!")
firebase_verifyemail((data["idToken"])
```
