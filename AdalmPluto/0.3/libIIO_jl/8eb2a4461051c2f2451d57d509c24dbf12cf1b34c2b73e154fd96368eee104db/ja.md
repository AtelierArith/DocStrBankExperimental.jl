```
C_iio_create_xml_context_mem(xml, length)
```

メモリ内のXMLデータからコンテキストを作成します。

# パラメータ

  * `xml::String` : メモリ内のXMLデータへのポインタ
  * `length::UInt` : メモリ内のXML文字列の長さ（最後の を除く）

# 戻り値

  * 成功した場合、iio_context構造体へのポインタ
  * 失敗した場合、アサーションが有効な場合はエラーがスローされます。
  * 失敗した場合、アサーションが無効な場合はNULLが返されます。

# 注意

XMLの形式は、`iio_context_get_xml`によって返される形式に準拠している必要があります。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Context.html#gabaa848ca554af5723a44b9b7fd0ba6a3)
