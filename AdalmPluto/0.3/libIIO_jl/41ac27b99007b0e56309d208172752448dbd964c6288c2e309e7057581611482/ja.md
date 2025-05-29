```
C_iio_context_get_attr(context, index)
```

コンテキスト固有の属性の名前と値を取得します。

# パラメータ

  * `context::Ptr{iio_context}` : iio_context 構造体へのポインタ
  * `index::UInt32` : 属性に対応するインデックス

# 戻り値

  * 成功した場合、`(0, name::String, value::String)` が返されます。
  * エラーの場合、`(errno, "", "")` が返されます。ここで、errno は負のコードです。

バージョン 0.9 で導入されました。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Context.html#ga477dfddaefe0acda401f600247e13fc7)
