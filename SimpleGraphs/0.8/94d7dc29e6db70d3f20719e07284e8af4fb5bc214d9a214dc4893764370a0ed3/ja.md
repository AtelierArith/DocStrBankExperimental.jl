`embed(G)` は `G` の新しい埋め込みを作成します。完全な呼び出しは次のとおりです。

```
embed(G,algorithm;args...)
```

`symbol` アルゴリズムは埋め込みアルゴリズムを示します。`args` はアルゴリズムに送信される可能性のある引数のコレクションです。

`algorithm` のデフォルトは `:circular` で、次のいずれかになります。

  * `:circular`: 頂点を円の中に均等に配置します。
  * `:random`: 頂点をランダムに配置します。
  * `:spring`: `GraphLayout` の `spring` レイアウトを使用します。オプションの引数：

      * `iterations`。
  * `:stress`: `GraphLayout` の `stress` レイアウトを使用します。
  * `:spectral`: `spectral` 埋め込みを使用します。オプションの引数：

      * `xcol` – `x` 座標に使用する固有値。
      * `ycol` – `y` 座標に使用する固有値。
  * `:normalized_spectral`: `spectral` と同じですが、代わりに `normalized_laplace` を使用します。
  * `:tutte` – 最長の面を使用して Tutte 埋め込みを作成します（グラフに回転システムがあると仮定）。

      * `outside` [オプション] – 埋め込みの外面となる頂点のリスト。

グラフがすでに（例えば）埋め込みを持っている場合、その埋め込みはアルゴリズムのいずれかの出発点として使用される可能性があることに注意してください。
