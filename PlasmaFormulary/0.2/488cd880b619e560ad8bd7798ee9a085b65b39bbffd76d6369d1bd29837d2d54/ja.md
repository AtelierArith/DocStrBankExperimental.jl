```
plasma_frequency(n::NumberDensity, [q::Charge, mass::Mass])
plasma_frequency(n::NumberDensity, p::ParticleLike; kw...)
```

種のプラズマ周波数を計算します。

プラズマ周波数はプラズマの特性周波数です。より一般的には、プラズマ内の電子が振動する周波数を指します。

# 例

```jldoctest; filter = r"(\^-1|⁻¹)"
julia> plasma_frequency(1e19u"m^-3")  # プラズマ周波数
1.7839863654934653e11 rad s⁻¹

julia> plasma_frequency(1e19u"m^-3", :p)  # 陽子のプラズマ周波数
4.1632945624883513e9 rad s⁻¹
```

# 参考文献

  * [Wikipedia](https://en.wikipedia.org/wiki/Plasma_oscillation)
  * [PlasmaPy Documentation](https://docs.plasmapy.org/en/latest/api/plasmapy.formulary.frequencies.plasma_frequency.html)

```
