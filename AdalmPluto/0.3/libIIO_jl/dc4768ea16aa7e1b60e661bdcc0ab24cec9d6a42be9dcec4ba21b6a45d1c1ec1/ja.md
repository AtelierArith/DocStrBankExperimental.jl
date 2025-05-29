```
C_iio_create_xml_context(xml_file)
```

XMLファイルからコンテキストを作成します。

# パラメータ

  * `xml_file::String` : 開くXMLファイルへのパス

# 戻り値

  * 成功した場合、iio_context構造体へのポインタ
  * 失敗した場合、アサーションが有効な場合はエラーがスローされます。
  * 失敗した場合、アサーションが無効な場合はNULLが返されます。

# 注意

XMLの形式は、`iio_context_get_xml`によって返される形式に準拠している必要があります。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Context.html#ga9925a84e596c3003e30b1cdd2b65d029)
