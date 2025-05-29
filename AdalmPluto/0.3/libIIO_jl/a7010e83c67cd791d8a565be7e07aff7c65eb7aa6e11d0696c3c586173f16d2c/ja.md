```
C_iio_device_create_buffer(device, samples_count, cyclic)
```

指定されたデバイスに関連付けられた入力または出力バッファを作成します。

# パラメータ

  * `device::Ptr{iio_device}`: iio_device 構造体へのポインタ
  * `samples_count::UInt` : バッファが含むべきサンプルの数
  * `cyclic::Bool` : True の場合、サイクリックモードを有効にします

# 戻り値

  * 成功した場合、iio_buffer 構造体へのポインタ
  * エラーの場合、アサーションが有効になっているときはエラーをスローします。
  * エラーの場合、アサーションが無効になっているときは NULL を返します。

# 注意

書き込みまたは読み取りを行う必要があるチャネルは、バッファを作成する前に有効にする必要があります。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Buffer.html#gaea8067aca27b93a1260a0c563607a501)
