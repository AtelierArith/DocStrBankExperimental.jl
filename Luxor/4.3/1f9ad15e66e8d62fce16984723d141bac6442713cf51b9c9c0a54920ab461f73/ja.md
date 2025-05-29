```
squircle(center::Point, hradius, vradius;
    action=:none,
    rt = 0.5, stepby = pi/40, vertices=false)
squircle(center::Point, hradius, vradius, action;
    rt = 0.5, stepby = pi/40, vertices=false)
```

スクワイアまたはスーパーロップス（基本的には角が丸い長方形）を作成します。中心位置、水平半径（中心から側面までの距離）、および垂直半径（中心から上または下までの距離）を指定します：

ルート（`rt`）オプションのデフォルトは0.5で、中間的な形状を提供します。0.5未満の値は形状をより長方形にし、0.5を超える値は形状をより丸くします。水平および垂直半径は異なることができます。

この関数は一連の点を生成し、ポリゴンを作成するか、Pointsの配列を返します。

関連情報：`polysuper()`および`squirclepath()`。
