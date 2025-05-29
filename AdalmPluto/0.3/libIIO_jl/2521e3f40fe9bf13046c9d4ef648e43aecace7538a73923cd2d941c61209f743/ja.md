```
C_iio_channel_attr_read_all()
```

これはプレースホルダーです。以下のドキュメントはCドキュメントのコピー/ペーストです。

すべてのチャネル固有の属性の内容を読み取ります。

# パラメータ

  * chn : iio_channel構造体へのポインタ
  * cb : コールバック関数へのポインタ
  * data : コールバック関数に渡されるポインタ

# 戻り値

  * 成功した場合、0が返されます
  * エラーの場合、負のerrnoコードが返されます

# 注意

この関数は、すべてのチャネル固有の属性が1つのコマンドで読み取られるため、ネットワークバックエンドと一緒に使用する際に特に便利です。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Channel.html#gab9c28b0cd94c0607bcc7cac16219eb48)
