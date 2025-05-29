```
arc(centerpoint::Point, radius, angle1, angle2; action=:none)
arc(centerpoint::Point, radius, angle1, angle2, action)
```

`angle1`から`angle2`まで時計回りに、`centerpoint`を中心に現在のパスに弧を追加します。

角度はx軸に対して定義され、正の方向は時計回りです。

関連: `carc()`, `arc2r()`, `arc2sagitta()`, ...
