```
currentserver(client::PCloudClient; kwargs...)
```

現在接続しているサーバーの `ip` と `hostname` を返します。ホスト名は、同じサーバーを指すIPアドレスのみを解決することが保証されています。この呼び出しは、アップロードの進行状況を追跡する必要があるときに便利です。

ソース: https://docs.pcloud.com/methods/general/currentserver.html

# 出力

  * `ip::String`: サーバーのIP v.4アドレス
  * `ipbin::String`: IP v.4アドレス
  * `ipv6::String`: サーバーのIP v.6アドレス
  * `hostname::String`: サーバーのホスト名

# 出力例

```
{
    ipv6: "::1",
    hostname: "api7.pcloud.com",
    ip: "204.155.155.21",
    result: 0,
    ipbin: "204.155.155.60"
}
```
