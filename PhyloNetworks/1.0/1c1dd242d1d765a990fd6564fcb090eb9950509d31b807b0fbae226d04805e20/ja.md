```
treeedgecomponents(net::HybridNetwork)
```

セミ指向ネットワークのツリーエッジコンポーネントを `membership` 辞書 `Node => Int` として返します。同じメンバーシップ整数値を持つノードは同じツリーエッジコンポーネントに属します。ネットワークのツリーエッジコンポーネントは、すべてのハイブリッドエッジが削除されたときのネットワークの連結成分です。

サイクルがツリーエッジコンポーネントのいずれかに存在する場合、またはツリーエッジコンポーネントに複数の「エントリー」ハイブリッドノードがある場合、`RootMismatch` エラーがスローされます。

警告:

  * `Node` は可変であるため、出力 `membership` 辞書の使用が終了するまでネットワークを変更しないでください。
  * コンポーネントIDは予測できませんが、コンポーネントの数に応じて1から始まる連続した整数になります。
