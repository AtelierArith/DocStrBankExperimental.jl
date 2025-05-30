```
lineto!(builder, pt)
```

現在のペンの位置からターゲットポイントptまでの線を生成します。`moveto!()`の後に続きます（2D、3D）。ptは既存のポイントインデックスまたはポイント座標のテーブルのいずれかです。後者の場合、ポイントが追加されます。ターゲットポイントのインデックスを返します。

# 例 2D: 異なるfacetregion番号で四角形を描く

```
 p = moveto!(b,[0,0])
 facetregion!(b,1);  lineto!(b,[1,0])
 facetregion!(b,2);  lineto!(b,[1,1])
 facetregion!(b,3);  lineto!(b,[0,1])
 facetregion!(b,4);  lineto!(b,p)
```

# 例 3D: 異なるfacetregion番号の2つの平面ファセット

```
 facetregion!(b,1);
 p1 = moveto!(b,[0,0,0])
 p2 = moveto!(b,[1,0,0])
 p3 = moveto!(b,[1,1,0])
 p4 = moveto!(b,[0,1,0])
 polyfacet!(b,[p1,p2,p3,p4])

 facetregion!(b,2);
 p1 = moveto!(b,[0,0,1])
 p2 = moveto!(b,[1,0,1])
 p3 = moveto!(b,[1,1,1])
 p4 = moveto!(b,[0,1,1])
 polyfacet!(b,[p1,p2,p3,p4])
```
