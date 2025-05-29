```
C_iio_device_find_channel(device, name, isOutput)
```

名前またはIDによってチャネル構造体を見つけようとします。

# パラメータ

  * `device::Ptr{iio_device}` : iio_device構造体へのポインタ
  * `name::String`            : 検索するチャネルの名前またはIDに対応するNULL終端文字列
  * `isOutput::Bool`          : 検索するチャネルが出力の場合はTrue、そうでない場合はFalse

# 戻り値

  * 成功した場合、iio_channel構造体へのポインタ
  * 失敗した場合、アサーションが有効な場合はエラーをスローします。
  * 失敗した場合、アサーションが無効な場合はNULLを返します。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#gaffc6086189ba801ab5e95341d68f882b)
