```
PointVariableBlockHeader{T,N}
```

`PointVariableBlockHeader`は、メッシュブロック内の指定されたポイントに対して相対的に位置する変数を記述するために使用されます。

ブロックヘッダーには、`base_header`（`BlockHeader`）と以下のメタデータが含まれています。

  * `mult`: 変数データに適用される正規化係数。
  * `units`: 正規化係数が適用された後のこの変数の単位。
  * `mesh_id`: このブロックのデータが定義されているメッシュに対する名前（`id`）。
  * `np`: ポイントの数。

グリッドベースの変数と同様に、書き込まれるデータには、メッシュ上の各ポイントでの指定された変数の値が含まれています。空間内の各ポイントの位置が完全に知られているため、スタッガー変数は必要ありません。データは`np`要素を持つ1次元配列の形式です。
