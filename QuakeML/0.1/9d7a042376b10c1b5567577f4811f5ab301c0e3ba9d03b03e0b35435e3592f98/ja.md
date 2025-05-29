```
quakeml(qml::EventParameters; version="1.2") -> xml::EzXML.XMLDocument
```

`EventParameters`型のイベントのセットである`qml`からXMLドキュメントを作成します。`xml`は出力に適した`EzXML.XMLDocument`です。

ユーザーは作成されるQuakeMLの名目上の`version`を設定することもできます。

QuakeMLドキュメント`xml`は`write(io, xml)`で書き込むことができるか、`string(xml)`で文字列に変換することができます。
