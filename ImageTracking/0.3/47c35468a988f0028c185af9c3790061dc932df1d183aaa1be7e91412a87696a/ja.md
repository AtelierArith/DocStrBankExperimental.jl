```
features = haar_features(img, top_left, bottom_right, feat)
features = haar_features(img, top_left, bottom_right, feat, coordinates)
```

指定された領域内の与えられた積分画像に対するHaar-like特徴を含む配列を返します。領域は、top*leftおよびbottom*rightのポイントによって指定され、特定の特徴タイプ（例：横に並んだ2つの長方形(:x2)）が指定されます。この関数は、特定の長方形構成に対するすべての可能な位置、および特定の特徴の座標が提供されていない場合はすべての可能な長方形の幅と高さに対して、すべてのHaar長方形特徴の値を計算します。座標が提供されている場合は、指定された座標の特徴の値のみを計算します。Haar長方形特徴の値を計算することは、特徴を構成する異なる長方形内のすべてのポイントの合計の差を見つけることに対応します。

パラメータ：

  * img               = Haar-like特徴を見つけるための積分画像
  * top_left          = 特徴を見つける領域の最上部および左端のポイント
  * bottom_right      = 特徴を見つける領域の最下部および右端のポイント
  * feat              = 見つけるHaar-like特徴のタイプを指定するシンボル

```
    現在、featは5つの値を取ることができます：

    :x2 = 水平軸に沿った2つの長方形
        +---------------------------------------+
        |                                       |
        | +-----+-----+                         |
        | |     |     |                         |
        | | -1  | +1  |  +---------->           |
        | |     |     |                         |
        | +-----+-----+                         |
        |                                       |
        |       +                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       v                               |
        |                                       |
        |                                       |
        |                                       |
        |                                       |
        |                                       |
        |                                       |
        +---------------------------------------+

    :y2 = 垂直軸に沿った2つの長方形
        +---------------------------------------+
        |                                       |
        | +------------+                        |
        | |     -1     |                        |
        | +------------+  +---------->          |
        | |     +1     |                        |
        | +------------+                        |
        |                                       |
        |       +                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       v                               |
        |                                       |
        |                                       |
        |                                       |
        |                                       |
        |                                       |
        |                                       |
        +---------------------------------------+

    :x3 = 水平軸に沿った3つの長方形
        +---------------------------------------+
        |                                       |
        | +-----+-----+-----+                   |
        | |     |     |     |                   |
        | | -1  | +1  | -1  |  +---------->     |
        | |     |     |     |                   |
        | +-----+-----+-----+                   |
        |                                       |
        |       +                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       v                               |
        |                                       |
        |                                       |
        |                                       |
        |                                       |
        |                                       |
        |                                       |
        +---------------------------------------+

    :y3 = 垂直軸に沿った3つの長方形
        +---------------------------------------+
        |                                       |
        | +------------+                        |
        | |     -1     |                        |
        | +------------+                        |
        | |     +1     |  +---------->          |
        | +------------+                        |
        | |     -1     |                        |
        | +------------+                        |
        |                                       |
        |       +                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       v                               |
        |                                       |
        |                                       |
        |                                       |
        |                                       |
        +---------------------------------------+

    :xy4 = 水平および垂直軸に沿った4つの長方形
        +---------------------------------------+
        |                                       |
        | +-----+-----+                         |
        | |     |     |                         |
        | | -1  | +1  |                         |
        | |     |     |                         |
        | +-----+-----+  +---------->           |
        | |     |     |                         |
        | | +1  | -1  |                         |
        | |     |     |                         |
        | +-----+-----+                         |
        |                                       |
        |       +                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       v                               |
        |                                       |
        |                                       |
        +---------------------------------------+

    +1および-1の符号は、最終的なHaar特徴を評価するためにどの長方形が減算され、どの長方形が加算されるかを示しています。

```

  * coordinates       = ユーザーは、特定のHaar-like特徴のみを見つけるために長方形の座標を提供できます。必要な形式は、(f,r,4)の3次元配列で、f = 特徴の数、r = 長方形の数、4は長方形のtop*leftおよびbottom*rightポイントの座標（top*left*y, top*left*x, bottom*right*y, bottom*right*x）用です。デフォルト値は何も指定されていない場合で、すべての特徴が見つかります。

## 参考文献

M. Oren, C. Papageorgiou, P. Sinha, E. Osuna and T. Poggio, "Pedestrian detection using wavelet templates," Proceedings of IEEE Computer Society Conference on Computer Vision and Pattern Recognition, San Juan, 1997, pp. 193-199.

P. Viola and M. Jones, "Rapid object detection using a boosted cascade of simple features," Proceedings of the 2001 IEEE Computer Society Conference on Computer Vision and Pattern Recognition. CVPR 2001, 2001, pp. I-511-I-518 vol.1.
