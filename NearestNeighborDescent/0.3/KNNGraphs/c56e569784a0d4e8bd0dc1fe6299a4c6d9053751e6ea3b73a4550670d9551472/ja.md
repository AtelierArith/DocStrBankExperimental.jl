```
update_flag!(graph, v, i, new_flag)
```

ノード `v` の i 番目の出力エッジのフラグを更新します。新しいエッジを返します。フラグはエッジの順序に影響を与えないため、これによりヒープ不変が無効になることはありません。
