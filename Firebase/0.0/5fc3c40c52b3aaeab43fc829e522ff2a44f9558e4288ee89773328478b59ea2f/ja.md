firebase*changepassword(newpassword="", firebase*id*token=FIREBASE*ID_TOKEN)

パスワードの変更 ユーザーのパスワードは、Auth setAccountInfo エンドポイントに HTTP POST リクエストを発行することで変更できます。

# 例

`julia data = firebase_signin("ab669522@gmail.com","helloworld!!") firebase_changepassword("hellopaaji!!",data["idToken"]) data = firebase_signin("ab6695221@gmail.com","hellopaaji!!") firebase_changepassword("helloworld!!",data["idToken"])``
