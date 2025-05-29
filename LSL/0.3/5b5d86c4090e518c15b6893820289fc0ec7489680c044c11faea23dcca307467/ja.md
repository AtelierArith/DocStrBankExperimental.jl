```
XML(info::StreamInfo)
```

StreamInfoの全体を含むXMLドキュメント（LightXMLから）を返します。

これは、最上位要素が`<info>`であるXMLドキュメントを生成します。info要素には、StreamInfoインスタンスの各フィールドに対する1つの要素が含まれています。これには以下が含まれます：

  * コア要素`<name>`、`<type>`、`<channel_count>`、`<nominal_srate>`、`<channel_format>`、`<source_id>`
  * その他の要素`<version>`、`<created_at>`、`<uid>`、`<session_id>`、`<v4address>`、`<v4data_port>`、`<v4service_port>`、`<v6address>`、`<v6data_port>`、`<v6service_port>`
  * ユーザー定義のサブ要素を持つ拡張説明要素`<desc>`。
