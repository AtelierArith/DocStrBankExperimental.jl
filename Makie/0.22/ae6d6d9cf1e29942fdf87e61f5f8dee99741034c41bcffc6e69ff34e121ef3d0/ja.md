```
RectLight(color, r::Rect2[, direction = -normal])
RectLight(color, center::Point3f, b1::Vec3f, b2::Vec3f[, direction = -normal])
```

指定された色のRectLightを作成します。最初のコンストラクタは、xおよびy方向に拡張する`Rect2`から光を導出します。2番目は、`b1`と`b2`が幅と高さのベクトル（スケールを含む）を指定することで、矩形（またはより正確には平行四辺形）の`center`を指定します。

RectLightは、光の調整を簡素化するために`translate!`、`rotate!`、および`scale!`を実装していることに注意してください。

利用可能性：

  * GLMakieは`Shading = MultiLightShading`で使用できます

```
