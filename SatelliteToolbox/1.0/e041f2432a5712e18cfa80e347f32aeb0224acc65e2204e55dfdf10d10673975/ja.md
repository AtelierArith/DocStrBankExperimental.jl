```
ltan_to_raan(ltan::Union{Number, Time}, t::Union{Number, DateTime}) -> Float64
```

RAAN [0, 2π] [rad] を計算します。これにより、上昇ノードのローカル時間 (LTAN) が瞬間 `t` [UT1] で `ltan` になります。

`ltan` は、時間を示す `Number` として表現することも、`Time` オブジェクトとして表現することもできます。

`t` は、ユリウス日 [UT1] または `DateTime` [UT1] として表現することができます。
