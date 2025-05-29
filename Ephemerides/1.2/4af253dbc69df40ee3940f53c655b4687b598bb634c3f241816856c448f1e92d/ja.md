```
ephem_rotation6(eph::EphemerisProvider, from::Int, to::Int, time::Number)
```

1セットの軸（to）の6要素の向きの角度を、別の軸（from）に対して`time`で計算します。これは、J2000からのTDB/TCB秒で表現され、カーネルのタイムスケールに従います。

!!! note
    向きの角度については、逆変換を自動的に計算することはできません。つまり、PA440の向きがICRFに対して定義されている場合、このルーチンを使用してPA440からICRFへの回転を計算することはできません。

