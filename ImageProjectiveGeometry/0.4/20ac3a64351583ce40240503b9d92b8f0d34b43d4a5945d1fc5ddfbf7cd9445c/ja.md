matrix2angleaxis - 同次行列から角度-軸記述への変換

```
Usage: t = matrix2angleaxis(T)

Argument:   T - 4x4 同次変換行列、または 3x3 回転行列。
Returns:    t - 回転軸を与える 3x1 列ベクトルで、回転角度はラジアンで表される。
```

Tの左上の3x3回転成分のみが使用され、Tの翻訳成分は無視されます。

関連: angleaxis2matrix(),  angleaxisrotate(), angleaxis(), normaliseangleaxis()
