```
plasma_beta(T, n, B)
```

プラズマベータ (β) を計算します。これは、熱圧と磁圧の比です。

# 引数

  * `T`: プラズマの温度。
  * `n`: プラズマの粒子密度。
  * `B`: プラズマの磁場。

# 例

```jldoctest
julia> plasma_beta(1e6u"K", 1e19u"m^-3", 0.2u"T")
0.008674873511172188
```

# 参考文献

  * [PlasmaPy Documentation](https://docs.plasmapy.org/en/stable/api/plasmapy.formulary.dimensionless.beta.html)
  * [Wikipedia](https://en.wikipedia.org/wiki/Plasma_beta)
