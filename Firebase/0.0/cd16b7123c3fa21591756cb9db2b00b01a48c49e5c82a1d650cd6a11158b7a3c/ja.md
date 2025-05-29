メール/パスワードでリンク 現在のユーザーにメール/パスワードをリンクするには、Auth setAccountInfoエンドポイントにHTTP POSTリクエストを発行します。

# 例

```julia
data = firebase_signin("ab669522@gmail.com","helloworld!!")
firebase_linkuserinfo("ash@gmail.com", "hello!!123as",data["idToken"])
data = firebase_signin("ash@gmail.com", "hello!!123as")
firebase_linkuserinfo("ab669522@gmail.com","helloworld!!",data["idToken"])
```
