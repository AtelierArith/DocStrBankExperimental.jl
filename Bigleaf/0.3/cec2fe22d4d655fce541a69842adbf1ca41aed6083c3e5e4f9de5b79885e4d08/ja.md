```
air_density(Tair,pressure; ...)
```

湿った空気の空気密度を気温と圧力から求める_

# 引数

  * Tair:      気温 (℃)
  * pressure:  大気圧 (kPa)

オプション 

  * `constants=`[`BigleafConstants`](@ref)`()`: エントリを持つ辞書   Kelvin, kPa2Pa

# 詳細

空気密度 $\rho$ は次のように計算されます:

$$
\rho = {pressure \over Rd * Tair}
$$

# 値

空気密度 (kg m-3)

# 例

```@example doc
# 25℃および標準圧力 (101.325kPa) における空気密度
air_density(25,101.325)
```

# 参考文献

Foken, T, 2008: Micrometeorology. Springer, Berlin, Germany.
