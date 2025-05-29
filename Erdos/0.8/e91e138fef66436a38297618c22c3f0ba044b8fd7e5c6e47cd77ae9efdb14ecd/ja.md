```
ネットワーク
```

インデックス付きエッジを持ち、グラフ/頂点/エッジのプロパティを格納する可能性を持つグラフを表す型。

```
Network(n=0)
```

`n` 頂点とエッジなしで `Network` を構築します。

```
Network(adjmx::AbstractMatrix; selfedges=true, upper=false)
```

隣接行列 `adjmx` から `Network` を構築し、`adjmx` の各非ゼロ要素に対応するエッジを配置します。`selfedges=false` の場合、`adjmx` の対角要素は無視されます。`upper=true` の場合、`adjmx` の上三角部分のみが考慮されます。
