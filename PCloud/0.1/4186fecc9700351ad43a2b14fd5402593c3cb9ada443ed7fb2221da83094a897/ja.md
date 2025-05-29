```
userinvites(client::PCloudClient; kwargs...)
```

現在のユーザーの招待状のリストを取得します。

ソース: https://docs.pcloud.com/methods/auth/userinvites.html

# 出力

受け入れられた招待状に関する情報を含むリスト `invites` を返します。フォーマットは次のとおりです：

  * `email::String`: 招待されたユーザーのメールアドレス。セキュリティのため、メールの一部は隠されています。
  * `is_pending::Bool`: 招待状が保留中かどうか。

新しいユーザーは、招待されたユーザーが登録され、ユーザーがメールを確認したときに保留中でなくなったときに、このリストに追加されます。

# 出力例

```
{
    "invites": [
    {
        "email": "x**@xyz.com",
        "is_pending": 1
    },

    ...

    ] , 
    result: 0
}
```
