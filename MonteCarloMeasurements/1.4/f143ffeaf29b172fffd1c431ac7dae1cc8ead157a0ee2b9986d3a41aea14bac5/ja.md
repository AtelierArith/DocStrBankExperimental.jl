```
pn = with_nominal(p, val)
```

粒子 `p` に名目値 `val` を付与します。`val` に最も近い粒子が `val` で置き換えられ、インデックス 1 に移動します。この操作は `pn` の統計にわずかなバイアスを導入しますが、大きなサンプルサイズに対しては漸近的にバイアスがありません。`pn` の名目値を取得するには、`nominal(pn)` を呼び出してください。
