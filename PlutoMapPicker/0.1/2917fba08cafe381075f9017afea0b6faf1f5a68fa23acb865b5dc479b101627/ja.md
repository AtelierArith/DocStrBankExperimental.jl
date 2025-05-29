Leafletマップで使用できるタイルレイヤー。

構成には以下が含まれます：

  * `url`: タイルをリクエストするためのURLテンプレート
  * `options`: タイルの最小および最大ズームレベルなどの追加構成を含む`Dict`。これはHypertextLiteralを使用してJavascriptオブジェクトに補間されます。

この構成はleafletでTileLayerを作成するために使用されます。URLテンプレートや利用可能なオプションについては、[leafletのTileLayerドキュメント](https://leafletjs.com/reference.html#tilelayer)を参照してください。
