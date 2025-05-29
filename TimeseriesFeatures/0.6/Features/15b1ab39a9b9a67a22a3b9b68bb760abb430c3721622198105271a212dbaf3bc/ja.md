`AbstractFeature` は緩いインターフェースを持っています。異なる機能のために (𝑓::AbstractFeature)(x) をオーバーロードします。他の `TimeseresFeatures` タイプとの互換性のために、次のように定義します：

## ヘルパーメソッド：

  * `getmethod(𝑓::AbstractFeature)`
  * `getname(𝑓::AbstractFeature)`
  * `getkeywords(𝑓::AbstractFeature)`
  * `getdescription(𝑓::AbstractFeature)`
