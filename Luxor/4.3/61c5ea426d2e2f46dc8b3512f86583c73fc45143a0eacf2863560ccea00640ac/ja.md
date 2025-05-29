```
ellipse(centerpoint::Point, w, h; action=:none)
ellipse(centerpoint::Point, w, h; action)
```

`centerpoint`を中心とし、幅`w`、高さ`h`の楕円を作成し、現在のパスに追加します。

楕円を囲むバウンディングボックスの隅の2つの点のタプルを返します。

関連: `circle()`, `squircle()`, `ellipseinquad()`...
