```
cutord(t1::TPS, order::Integer)
```

指定された次数以上のモノミオを`t1`からカットします。あるいは、`order`が負の場合は、`abs(order)`以下の次数のモノミオをカットします。

# 例

```julia-repl
julia> d = Descriptor(1, 10);

julia> Δx = first(@vars(d));

julia> cutord(sin(Δx), 5)
TPS64{Descriptor(NV=1, MO=10)}:
 Coefficient                Order   Exponent
  1.0000000000000000e+00      1      1
 -1.6666666666666666e-01      3      3


julia> cutord(sin(Δx), -5)
TPS64{Descriptor(NV=1, MO=10)}:
 Coefficient                Order   Exponent
 -1.9841269841269841e-04      7      7
  2.7557319223985893e-06      9      9
```
