```
DiNetwork
```

インデックス付きエッジを持ち、グラフ/頂点/エッジのプロパティを格納する可能性のある有向グラフを表す型です。

```
DiNetwork(n=0)
```

`n` 頂点とエッジなしで `DiNetwork` を構築します。

```
DiNetwork(adjmx::AbstractMatrix; selfedges=true)
```

隣接行列 `adjmx` から `DiNetwork` を構築します。`selfedges=false` の場合、`adjmx` の対角要素は無視されます。
