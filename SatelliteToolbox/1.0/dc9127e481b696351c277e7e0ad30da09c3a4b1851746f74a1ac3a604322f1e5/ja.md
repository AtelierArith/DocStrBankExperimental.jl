```
ltdn_to_raan(ltdn::Union{Number, Time}, t::Union{Number, DateTime}) -> Float64
```

降下ノードのローカル時間 (LTAN) が `ltdn` である瞬間 `t` [UT1] において、RAAN [0, 2π] [rad] を計算します。

`ltdn` は、時間を示す `Number` として表現することも、`Time` オブジェクトとして表現することもできます。

`t` は、ユリウス日 [UT1] または `DateTime` [UT1] として表現することができます。
