```
phnprb(corpus::Array, frequencies::Array, queries::Array; positional=false,
    nchar=1, pad=true)
```

コーパスに基づいて、クエリのリスト内の各アイテムの音韻確率を計算します。

# 引数

  * **corpus** 確率計算の基礎となるコーパス
  * **frequencies** `corpus`内の各要素に関連付けられた頻度
  * **queries** 確率を計算するアイテム

## キーワード引数

  * **positional** 特定の音がクエリ内のどこに現れるかを考慮するかどうか

（例：最初の音としての「K」と、2番目の音としての「K」を異なるカテゴリとして考慮すべきか？）

  * **nchar** 検査される各n-グラムの文字数（例：二重音のための2）
  * **pad** 各クエリにパディングを追加するかどうか

# 戻り値

クエリが最初の列に、確率値が2番目の列にある`DataFrame`。
