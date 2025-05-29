```
logout(client::PCloudClient; kwargs...)
```

`token`を取得し、それを無効にします。

ソース: https://docs.pcloud.com/methods/auth/logout.html

# 出力

`token`の無効化が成功した場合、bool `auth_deleted`を返します

（`token`が正しく、実際に無効にされた場合）。

# 出力例

```
{
    result: 0,
    auth_deleted: true
}
```
