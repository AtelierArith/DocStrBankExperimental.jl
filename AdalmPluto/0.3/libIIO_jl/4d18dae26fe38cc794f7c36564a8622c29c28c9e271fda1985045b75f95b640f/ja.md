```
C_iio_channel_enable(channel)
```

指定されたチャネルを有効にします。

# パラメータ

  * `channel::Ptr{iio_channel}` : iio_channel 構造体へのポインタ

# 注意

`iio*device*create*buffer` を使用して iio*buffer 構造体を作成する前に、デバイスから読み取るために少なくとも1つのチャネルを有効にする必要があります。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Channel.html#ga2b787983683d37966b5e1e5c6c121d6a)
