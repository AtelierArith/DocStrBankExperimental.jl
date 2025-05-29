```
ExchangeGraph(snd; symmetric=false [rcv, neighbors,find_rcv_ids])
```

`snd`の出力隣接リストのみから`ExchangeGraph`オブジェクトを作成します。受信隣接リストが既知の場合は、`rcv`を設定することでキーワード引数として渡すことができ、他のキーワード引数は無視されます。`symmetric==true`の場合、受信隣接リストは`snd`に設定されます。それ以外の場合、オプションの`neighbors`または`find_rcv_ids`が考慮されます（その順序で）。`neighbors`は`snd`に関連する出力および受信隣接のスーパーセットを含む別の`ExchangeGraph`です。これは、受信隣接リスト`rcv`を効率的に見つけるために使用されます。`neighbors`が提供されていない場合、`find_rcv_ids`が使用されます（ユーザー提供のものまたはデフォルトのもの）。`find_rcv_ids`は、snd側の情報から交換グラフのrcv側を見つけるアルゴリズムを実装した関数です。
