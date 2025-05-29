```
invite(client::PCloudClient; kwargs...)
```

ユーザー登録時にユーザーアカウントに無料スペースを付与するリファラーコードを持つ登録ページのURLを取得します。

ソース: https://docs.pcloud.com/methods/auth/invite.html

# 出力

  * `url::String`: 登録ページのアドレス
  * `spacelimitreached::Bool`: ユーザーによって無料スペースの最大値に達しているかどうか。

# 出力例

```
{
    url: "https://my.pcloud.com/#page=register&invite=invite_code",
    spacelimitreached: false,
    result: 0
}
```
