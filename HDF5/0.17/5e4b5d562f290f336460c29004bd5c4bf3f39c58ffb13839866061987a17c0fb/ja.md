```
dataspace(data)
```

デフォルトの `Dataspace` は、Julia オブジェクト `data` を表すために使用されます：

  * 文字列または数値：スカラー `Dataspace`
  * 配列：シンプルな `Dataspace`
  * `struct` 型：スカラー `Dataspace`
  * `nothing` または `EmptyArray`：ヌルデータスペース
