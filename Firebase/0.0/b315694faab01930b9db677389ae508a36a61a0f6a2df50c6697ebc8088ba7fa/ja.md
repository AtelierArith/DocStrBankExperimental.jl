firebase*changeemail(newemail="",firebase*id*token=  FIREBASE*ID_TOKEN)

メールアドレスの変更 ユーザーのメールアドレスは、Auth setAccountInfo エンドポイントに HTTP POST リクエストを発行することで変更できます。

# 例

`julia data = firebase_signin("ab669522@gmail.com,"helloworld!!") firebase_changeemail("ab6695221@gmail.com",data["idToken"]) data = firebase_signin("ab6695221@gmail.com,"helloworld!!") firebase_changeemail("ab669522@gmail.com",data["idToken"])``
