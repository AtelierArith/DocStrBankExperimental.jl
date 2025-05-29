```
ephem_vector12(eph::EphemerisProvider, from::Int, to::Int, time::Number)
```

1つの天体（to）の12要素の状態を別の天体（from）に対して`time`で計算します。これは、J2000からのTDB/TCB秒で表現され、カーネルの時間スケールに従います。
