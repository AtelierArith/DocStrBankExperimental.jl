```
userinfo(client::PCloudClient; kwargs...)
```

現在のユーザーに関する情報を返します。特定の `login` メソッドがないため、資格情報は任意のメソッドに渡すことができ、特に特定のアクションを考えずにログインするのに適した場所です。

Source: https://docs.pcloud.com/methods/general/userinfo.html

# 出力

  * `email::String`: ユーザーのメールアドレス
  * `emailverified::Bool`: ユーザーがメールを確認した場合は true
  * `registered::datetime`: ユーザーが登録された日時
  * `premium::Bool`: ユーザーがプレミアムの場合は true
  * `premiumexpires::datetime`: プレミアムが true の場合: premiumexpires はサービスが有効な日付
  * `quota::Int`: バイト単位
  * `usedquota::Int`: バイト単位、かなり大きな数値
  * `language::String`: 2-3 文字の小文字の言語 ID

# 出力例

```
{
    result: 0, 
    userid: 1234,
  email: pcloud@pcloud.com,
  emailverified: true,
  registered: "Mon, 18 Nov 2013 15:32:05 +0000",
  language: "en",
    premium: false,
  usedquota: 500,
  quota: 1000    
}
```
