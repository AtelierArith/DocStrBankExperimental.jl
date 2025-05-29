```
carc(centerpoint::Point, radius, angle1, angle2; action=:none)
carc(centerpoint::Point, radius, angle1, angle2, action)
```

`centerpoint`を中心とした弧を現在のパスに`angle1`から`angle2`まで、反時計回りに追加します。

角度はx軸に対して定義され、正の方向は時計回りです。

関連: `arc()`, `carc2r()`, `carc2sagitta()`, ...
