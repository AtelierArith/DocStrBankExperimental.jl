normaliseangleaxis - 角度-軸記述子を正規化します。

関数は、角度-軸記述子と結果の回転との間の一対一の対応を確保するために、θを-πからπの範囲に収めるように正規化します。

```
Usage: t2 = normaliseangleaxis(t)

Argument:   t  - 3ベクトルで、回転軸を与え、その大きさはラジアンでの回転角度に等しい。
Returns:    t2 - 正規化された角度-軸記述子
```

参照: matrix2angleaxis(), angleaxis(), angleaxis2matrix(), angleaxisrotate()
