```
C_iio_create_local_context()
```

ローカルIIOデバイスからコンテキストを作成します（Linuxのみ）

# 戻り値

  * 成功した場合、iio_context構造体へのポインタ
  * 失敗した場合、アサーションが有効になっているとエラーがスローされます。
  * 失敗した場合、アサーションが無効になっているとNULLが返されます。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Context.html#gaf31acec2d0f9f498870cc52a1d49783e)
