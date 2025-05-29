```
converter = Converter(from_unit::Unit,to_unit::Unit)
```

`from_unit`の数値を`to_unit`の同等の値に変換するコンバータ関数を作成します。

```julia
using UDUnits
sys = System()
conv = Converter(sys["m/s"],sys["km/h"])
speed_in_m_per_s = 100.
speed_in_km_per_h = conv(speed_in_m_per_s)
```
