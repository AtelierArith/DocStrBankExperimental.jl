```
newpedlist,newidtable = set_upg(pedlist, idtable, upgtable)
```

未知の親グループ（UPG）を、系図リスト `pedlist` と元のIDテーブル `idtable` のルールに従って `upgtable` に従って未知の親に割り当てます。以下の例を参照してください。5つのUPGと、IDが「A」、「B」、「C」の動物が1番目のUPGにグループ化され、「D」と「E」が2番目のUPGにグループ化されます。

```
upgtable = Dict("A"=>1, "B"=>1, "C"=>1, "D"=>2, "E"=>2)
```

`upgtable` でUPGとして定義された「動物」は系図リストから削除されます。親動物がいる場合、それらは実際の動物の数より大きい整数のUPGコードに置き換えられます。テーブル `idtable` もそれに応じて更新されます。
