```
C_iio_device_get_name(device)
```

デバイス名を取得します（例：xadc）

# パラメータ

  * `device::Ptr{iio_device}` : iio_device構造体へのポインタ

# 戻り値

  * NULLで終わる文字列

# 注意

デバイスに名前がない場合、アサーションが有効になっているとエラーをスローします。デバイスに名前がない場合、アサーションが有効になっていると空の文字列を返します。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#ga711666b3b3b6314fbe7e592b4632ab85)
