帯電粒子が均一な磁場中での円運動の半径を計算する

参考文献: [PlasmaPy API Documentation](https://docs.plasmapy.org/en/latest/api/plasmapy.formulary.lengths.gyroradius.html)

# 例

```jldoctest
julia> gyroradius(0.2u"T", Unitful.me, Unitful.q, 1e6u"K")
0.00015651672339994665 m
```
