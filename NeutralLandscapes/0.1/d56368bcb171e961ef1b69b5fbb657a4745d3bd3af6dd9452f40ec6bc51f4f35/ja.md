```
WaveSurface <: NeutralLandscapeMaker

WaveSurface(; direction=360rand(), periods=1)
WaveSurface(direction, [periods=1])
```

指定された`direction`と`periods`の数を持つ正弦波の風景を作成します。どちらも指定されていない場合、ランダムな方向の単一の周期が生成されます。
