```
C_iio_channel_get_name(channel)
```

チャネル名を取得します（例：vccint）

# パラメータ

  * `channel::Ptr{iio_channel}` : iio_channel 構造体へのポインタ

# 戻り値

  * NULL で終わる文字列。

# 注意

チャネルに名前がない場合、アサーションが有効になっているとエラーをスローします。アサーションが無効になっている場合、空の文字列を返します。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Channel.html#ga37346a6f3fcfb1eb40572aec6c3b39ac)
