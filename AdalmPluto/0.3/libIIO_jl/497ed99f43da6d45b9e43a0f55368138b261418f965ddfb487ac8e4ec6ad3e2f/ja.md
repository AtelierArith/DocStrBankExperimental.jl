```
C_iio_device_get_sample_size(device)
```

現在のサンプルサイズを取得します。

# パラメータ

  * `device::Ptr{iio_device}` : iio_device 構造体へのポインタ

# 戻り値

  * 成功した場合、バイト単位のサンプルサイズ
  * エラーの場合、負の errno コードが返されます

# 注意

サンプルサイズは一定ではなく、チャネルが有効または無効になると変更されます。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Debug.html#ga52b3e955c10d6f962b2c2e749c7c02fb)
