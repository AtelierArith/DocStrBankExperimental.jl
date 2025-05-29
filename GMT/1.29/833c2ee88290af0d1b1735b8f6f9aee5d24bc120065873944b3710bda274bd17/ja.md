```
getprovider(name, zoom::Int; variant="", date::String="", key::String="")
```

タイルプロバイダーの名前とズームレベルに基づいて情報を取得します。返される情報は内部使用のみに関連しており、ここでは文書化されていない実装の詳細です。

### 引数

  * `name`: タイルプロバイダーの名前。現在利用可能なのは「Bing」（デフォルト）、「Google」、「OSM」、「Esri」、「Nimbo」です。オプションとして、`name`は2つの文字列のタプルであり、最初の文字列がプロバイダー名、2番目の文字列がバリアント名（以下の`variant`を参照）であることができます。
  * `name`引数は、TileProviders.jlパッケージの`Provider`型でもあります。たとえば、TileProviders.jlをインポートした後、$provider = NASAGIBSTimeseries()$を作成し、次にそれを`getprovider`に渡します。
  * `date`: 現在は「Nimbo」プロバイダーでのみ使用されます。日付は「YYYY_MM」または「YYYY,MM」形式で渡します。
  * `key`: 現在は「Nimbo」プロバイダーでのみ使用されます。あなたのhttps://nimbo.earth/ APIキーを渡します。
  * `zoom`: 要求されたズームレベル。プロバイダーの最大値に制限されます。
  * `variant`: 複数の地図レイヤーを持つプロバイダーのオプションのバリアント。

      * `Bing`: variants => "Aerial"（デフォルト）、"Road"、または"Hybrid"。
      * `Google`: variants => "Satellite"、"Road"、"Terrain"、または"Hybrid"。
      * `Esri`: variants => "World*Street*Map"（デフォルト）、"Elevation/World*Hillshade"、または"World*Imagery"。
      * `Nimbo`: variants => "RGB"（デフォルト）、"NIR"、"NDVI"、または"RADAR"。

```
