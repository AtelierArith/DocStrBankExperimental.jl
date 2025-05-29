```
C_iio_device_buffer_attr_write_all()
```

これはプレースホルダーです。以下のドキュメントはCドキュメントのコピー/ペーストです。

すべてのバッファ特有の属性の値を設定します。

# パラメータ

  * dev : iio_device構造体へのポインタ
  * cb : コールバック関数へのポインタ
  * data : コールバック関数に渡されるポインタ

# 戻り値

  * 成功した場合、0が返されます
  * エラーの場合、負のerrnoコードが返されます

# 注意

この関数は、すべてのバッファ特有の属性が1つのコマンドで書き込まれるため、ネットワークバックエンドで使用する際に特に便利です。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#ga3d77bb90c22eb1d0a13805bf69def068)
