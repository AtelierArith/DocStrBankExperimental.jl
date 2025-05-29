```
drawTagAxes!(image, tag, CameraMatrix)
```

タグのx、y、z軸を描画して向きを示します。 `imageCol = RGB.(image) foreach(tag->drawTagAxes!(imageCol, tag, K), tags)`
