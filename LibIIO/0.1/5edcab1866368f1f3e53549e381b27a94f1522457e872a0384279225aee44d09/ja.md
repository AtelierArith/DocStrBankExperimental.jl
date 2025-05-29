```
Channel(dev::AbstractDeviceOrTrigger, channel::Ptr{iio_channel})
```

Channel型の新しいインスタンスを初期化します。

# パラメータ

  * `dev::AbstractDeviceOrTrigger` : 親デバイスハンドル（`Device`または`Trigger`）
  * `channel::Ptr{iio_channel}` : 有効なIIOチャネルへのポインタ。

# 戻り値

  * この型の新しいインスタンス
