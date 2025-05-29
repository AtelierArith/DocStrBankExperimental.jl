```
C_iio_channel_attr_write_all()
```

これはプレースホルダーです。以下のドキュメントはCドキュメントのコピー/ペーストです。

すべてのチャネル固有の属性の値を設定します。

# パラメータ

  * chn : iio_channel構造体へのポインタ
  * cb : コールバック関数へのポインタ
  * data : コールバック関数に渡されるポインタ

# 戻り値

  * 成功した場合、0が返されます
  * エラーの場合、負のerrnoコードが返されます

# 注意

この関数は、すべてのチャネル固有の属性が1つのコマンドで書き込まれるため、ネットワークバックエンドと一緒に使用する際に特に便利です。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Channel.html#ga6df693ee4f0c329d957f7c7ca3588f3f)
