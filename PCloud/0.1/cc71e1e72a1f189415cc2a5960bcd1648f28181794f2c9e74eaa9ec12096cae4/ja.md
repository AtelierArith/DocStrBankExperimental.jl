```
register(client::PCloudClient; kwargs...)
```

新しいユーザーアカウントを登録します

パラメータ `termsaccepted` は、ユーザーがサービス利用規約およびその他の合意に同意した場合、`yes` に設定する必要があります。

新しいパスワードは、changepassword と同じチェックの対象となります。

出典: https://docs.pcloud.com/methods/auth/register.html

# 引数

  * `mail::String`: ユーザーのメールアドレス
  * `password::String`: ユーザーが選択したパスワード

# オプション引数

  * `language::String`: サポートされている言語のいずれかに設定します。サポートされている言語を参照してください
  * `referer::String`: 参照元ユーザーのユーザーID

# 出力例

```
{
    "result": 0
}
```
