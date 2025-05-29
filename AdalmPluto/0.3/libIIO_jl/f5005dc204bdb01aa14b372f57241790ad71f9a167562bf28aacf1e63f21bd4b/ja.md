```
C_iio_context_get_attr_value(context, name)
```

コンテキスト固有の属性の値を取得します。

# パラメータ

  * `context::Ptr{iio_context}` : iio_context 構造体へのポインタ
  * `name::String` : 読み取るコンテキスト属性の名前

戻り値

  * 成功した場合、NULL で終わる文字列。
  * 名前が属性に対応しない場合、アサーションが有効になっているとエラーをスローします。
  * 名前が属性に対応しない場合、アサーションが無効になっていると空の文字列を返します。

バージョン 0.9 で導入されました。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Context.html#ga6394d108d425e4a6ed28d00c0e93d6ed)
