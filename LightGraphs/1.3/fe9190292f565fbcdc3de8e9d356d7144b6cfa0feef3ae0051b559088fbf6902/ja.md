```
bfs_parents(g, s[; dir=:out])
```

グラフ `g` の幅優先探索を頂点 `s` から開始します。頂点によってインデックス付けされた親頂点のベクトルを返します。`dir` が指定されている場合は、対応するエッジの方向を使用します（`:in` と `:out` は許容される値です）。

### パフォーマンス

この実装は大規模なグラフでの性能を考慮して設計されています。小規模なグラフでは実際にわずかに速い実装もありますが、大規模なグラフでこの実装を使用することで得られる性能向上は顕著です。
