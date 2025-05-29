**GBIF分類群の表現**

すべての分類学的レベルのフィールドは、`missing` であるか、分類群/レベルの名前をGBIFデータベース内の一意のキーにリンクするペアであることができます。

`name` - 分類群の一般名

`scientific` - 種の受け入れられた学名

`status` - 分類群のステータス

`match` - 一致のタイプ

`kingdom` - 王国の名前をその一意のIDにリンクする `Pair`

`phylum` - 門の名前をその一意のIDにリンクする `Pair`

`class` - 範疇の名前をその一意のIDにリンクする `Pair`

`order` - 順序の名前をその一意のIDにリンクする `Pair`

`family` - 科の名前をその一意のIDにリンクする `Pair`

`genus` - 属の名前をその一意のIDにリンクする `Pair`

`species` - 種の名前をその一意のIDにリンクする `Pair`

`confidence` - 一致の信頼度を示す `Int64`

`synonym` - 分類群が同義語であるかどうかを示す `Boolean`
