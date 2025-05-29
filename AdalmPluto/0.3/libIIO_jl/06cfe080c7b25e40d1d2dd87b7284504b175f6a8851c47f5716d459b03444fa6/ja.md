```
C_iio_context_find_device(context, name)
```

デバイス構造体をその名前またはIDで探します。

# パラメータ

  * `context::Ptr{iio_context}` : iio_context構造体へのポインタ
  * `name::String` : 検索するデバイスの名前またはIDに対応するNULL終端文字列

# 戻り値

  * 成功した場合、iio_device構造体へのポインタ
  * 名前またはIDが既知のデバイスに対応しない場合、アサーションが有効な場合はエラーがスローされ、そうでない場合はNULLが返されます。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Context.html#gade1dadfb5bc3c3b236add67f803c50c3)
