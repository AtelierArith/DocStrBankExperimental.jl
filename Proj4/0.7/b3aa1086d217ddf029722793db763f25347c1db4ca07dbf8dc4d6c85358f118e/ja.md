```
transform!(src_projection, dest_projection, position [, radians=false])
```

地理座標系または投影座標系の間で変換し、`position`をその場で修正します。

引数:

```
src      - ソース座標系の定義
dest     - 目的地座標系の定義
position - その場で変換される座標の配列。`position`が長さ2または3の
           ベクトルである場合、それは単一の点として扱われます。地理座標系の場合、
           最初の2列は*経度*と*緯度*で、その順序で表示されます。点の配列を
           変換するには、形状がNx2またはNx3の行列を使用できます。
radians  - trueの場合、地理的なlon,lat座標を入力および出力のラジアンとして扱います。
```

返り値:

```
position - 変換された位置
```
