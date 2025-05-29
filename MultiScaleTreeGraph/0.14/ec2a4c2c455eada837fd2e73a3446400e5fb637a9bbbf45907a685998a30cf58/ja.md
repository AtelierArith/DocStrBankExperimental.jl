```
new_id(mtg)
new_id(mtg, max_id)
```

最大ノードIDをインクリメントすることで新しい一意の識別子を作成します。ヒント: パフォーマンスのために、繰り返し行う場合は `max_id = max_id(mtg)` を使用し、その後 `new_id(mtg, max_id)` を使用することをお勧めします。
