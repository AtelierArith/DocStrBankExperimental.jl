```
drawTagAxes!(image, tag, CameraMatrix)
```

Draw the tag x, y, and z axes to show the orientation. `imageCol = RGB.(image) foreach(tag->drawTagAxes!(imageCol, tag, K), tags)`
