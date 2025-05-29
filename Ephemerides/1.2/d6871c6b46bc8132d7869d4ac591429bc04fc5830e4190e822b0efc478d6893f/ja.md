```
ephem_rotation3(eph::EphemerisProvider, from::Int, to::Int, time::Number)
```

1セットの軸（to）の3要素の向き角を、別の軸（from）に対して`time`において計算します。これは、J2000からのTDB/TCB秒で表現され、カーネルのタイムスケールに従います。

!!! note
    向き角については、逆変換を自動的に計算することはできません。つまり、PA440の向きがICRFに対して定義されている場合、このルーチンを使用してPA440からICRFへの回転を計算することはできません。

