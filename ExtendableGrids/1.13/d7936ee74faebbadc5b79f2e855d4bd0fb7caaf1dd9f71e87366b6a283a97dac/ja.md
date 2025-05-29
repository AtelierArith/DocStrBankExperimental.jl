```
simplexgrid(grid2d::ExtendableGrid, coordZ; bot_offset=0,cell_offset=0,top_offset=0, bface_offset=0)
```

2Dグリッドと1D座標配列のテンソル積を作成します。

セル領域と外側のファセット領域は2Dグリッドから引き継がれ、それぞれ`cell_offset`と`bface_offset`に追加されます。上部および下部ファセット領域はセル領域から検出され、それぞれ`bot_offset`および`top_offset`に追加されます。
