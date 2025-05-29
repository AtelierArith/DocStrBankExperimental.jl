```
union_ghost(indices,gids,owners)
```

`indices`内のゴーストインデックスのユニオンを、グローバルインデックス`gids`およびオーナー`owners`とともに作成します。新しいゴーストインデックスと`indices`内の同じオーナーインデックスを持つ、`indices`と同じ型のオブジェクトを返します。結果は`gids`および`owners`の所有権を持ちません。
