```
FresnelLens(insidematerial, frontvertex, radius, thickness, semidiameter, groovedepth; conic = 0.0, aspherics = nothing, outsidematerial = AGFFileReader.Air)
```

FresnelレンズをCSGオブジェクトとして作成します。凹面または凸面にすることができます。溝の位置は`groovedepth`に基づいて反復的に見つけられます。負の半径の場合、中央面の頂点は`frontvertex`にあり、レンズの総厚さは`thickness` + `groovedepth`です。**非球面は現在サポートされていません**。
