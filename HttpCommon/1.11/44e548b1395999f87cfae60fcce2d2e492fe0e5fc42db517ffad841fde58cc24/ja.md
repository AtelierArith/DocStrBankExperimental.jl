`Response`は、サーバーからクライアントに送信されるHTTPレスポンスを表します。以下の6つのフィールドがあります：

  * `status`: HTTPステータスコード（`STATUS_CODES`を参照）[デフォルト: `200`]
  * `headers`: `Headers` [デフォルト: `HttpCommmon.headers()`]
  * `cookies`: 文字列の辞書 => `Cookie`s
  * `data`: リクエストデータをバイトのベクターとして [デフォルト: `UInt8[]`]
  * `finished`: `Response`が有効である場合は`true`、つまり実際のHTTPレスポンスに変換できることを意味します [デフォルト: `false`]
  * `requests`: レスポンスを生成したリクエストの履歴。リダイレクトが関与している場合は1つ以上になることがあります。

`Response`には多くのコンストラクタがあります - 完全なリストは`methods(Response)`を使用してください。
