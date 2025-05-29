```
RectangularCluster <: NeutralLandscapeMaker

RectangularCluster(; minimum=2, maximum=4)
RectangularCluster(minimum, [maximum=4])
```

ランダムな値を含む長方形で風景を埋めます。各長方形/パッチのサイズは `minimum` と `maximum` の間であり（2つは固定サイズの長方形のために等しくすることができます）。
