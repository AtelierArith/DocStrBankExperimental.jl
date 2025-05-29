```
C_iio_create_network_context(host)
```

ネットワークからコンテキストを作成します。

# パラメータ

  * `host::String` : IIOデーモンが実行されているホスト名、IPv4またはIPv6アドレス

# 戻り値

  * 成功した場合、iio_context構造体へのポインタ
  * 失敗した場合、アサーションが有効になっているとエラーがスローされます。
  * 失敗した場合、アサーションが無効になっているとNULLが返されます。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Context.html#ga8adf2ef4d2b62aa34201469cd7049617)
