```
C_iio_device_identify_filename(device, filename)
```

ファイル名に対応するチャネルまたはデバッグ属性を特定します。

# パラメータ

  * `device::Ptr{iio_device}` : iio_device 構造体へのポインタ
  * `filename::String` : ファイル名に対応する NULL 終端文字列

# 戻り値

  * 成功した場合、`(0, channel::Ptr{iio_channel}, attribute::String)` が返されます。
  * エラーの場合、`(errno, NULL, "")` が返されます。ここで、errno は負のエラーコードです。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Debug.html#ga87ef46fa578c7be7b3e2a6f9f16fdf7e)
