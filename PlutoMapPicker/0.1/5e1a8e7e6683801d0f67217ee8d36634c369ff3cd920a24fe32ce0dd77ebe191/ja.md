タイルレイヤーは、Stadia Mapsからタイルを取得します。

詳細については、[Stadia Mapsのドキュメント](https://docs.stadiamaps.com/)を参照してください。

## スタイル

  * `osm_bright`: OpenStreetMapのレイアウトに似ています。
  * `outdoors`: `osm_bright`に似ていますが、公園、ハイキングコース、山などにより焦点を当てています。
  * `stamen_toner`: 高コントラストの白黒スタイルです。
  * `stamen_watercolor`: 水彩画のように見えます。

## 認証

Stadia Mapsへのリクエストは認証されておらず、APIキーを含んでいません。

執筆時点では、Stadia Mapsは`localhost`からの認証されていないリクエストを許可しています。これは、ローカルのPlutoノートブックからのリクエストなどです。ノートブックをオンラインでホストしたい場合は、Stadia MapsからAPIキーをリクエストし、APIキーを使用する`TileLayer`を作成する必要があります。
