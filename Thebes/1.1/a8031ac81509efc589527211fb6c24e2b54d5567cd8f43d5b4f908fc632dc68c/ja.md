```
 text3D(str, anchor::Point3D;
    halign=:left,
    valign=:baseline,
    about=Point3D(0., 0., 0.),
    rotation::Rotation=RotXYZ(0, 0, 0))
```

点 `pt` にテキストを描画し、x 軸の平面に配置します。`rotation` の角度は、デフォルトで `Point3D(0, 0, 0)` に設定された `about` 点の周りでテキストを回転させます。

Luxor の `fontface()` および `fontsize()` 設定を使用します。

次のような関数を使用して回転を指定します：

  * `RotX(a)`
  * `RotZ(a)`
  * `RotXZ(a1, a2)`
  * `RotXYZ(a1, a2, a3)`
