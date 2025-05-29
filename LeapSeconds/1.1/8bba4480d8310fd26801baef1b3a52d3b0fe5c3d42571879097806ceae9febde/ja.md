```
offset_utc_tai(utc1, utc2=0.0)
```

与えられたUTC擬似ユリウス日数`utc1`（精度向上のために2つの部分に分割することも可能）に対する協定世界時（UTC）と国際原子時（TAI）の差を返します。

$$
\Delta AT = UTC - TAI
$$

!!! note
    この関数は、うるう秒中のUTC日付を表すユリウス日数に対する[ERFA規約](https://github.com/liberfa/erfa/blob/master/src/dtf2d.c#L49)を使用します。

