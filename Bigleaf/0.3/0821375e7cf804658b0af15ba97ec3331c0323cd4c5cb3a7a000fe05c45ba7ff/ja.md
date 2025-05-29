```
psychrometric_constant(Tair,pressure; ...)
```

心理気象定数を計算します。

# 引数

  * Tair:      空気温度 (℃)
  * pressure:  大気圧 (kPa)

オプション 

  * `constants=`[`BigleafConstants`](@ref)`()`: エントリ cp, eps を持つ辞書

# 詳細

心理気象定数 ($\gamma$) は次のように与えられます：

$$
\gamma = cp * pressure / (eps * \lambda)
$$

ここで、$\lambda$ は蒸発潜熱 (J kg-1) であり、[`latent_heat_vaporization`](@ref) から計算されます。

# 値

心理気象定数 (kPa K-1)

# 参考文献

Monteith J.L., Unsworth M.H., 2008: Principles of Environmental Physics.             第3版. Academic Press, ロンドン。

# 例

```@example doc
psychrometric_constant.(5.0:5.0:25.0, 100)
```
