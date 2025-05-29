```
@traitdef HasNonFrequencyDimension{D}
```

データオブジェクトが非周波数ドメイン次元を持っているかどうかを示すトレイト。

# 例

```julia
@traitfn f(x::X) where {X; HasNonFrequencyDimension{X}} = "このスペクトルは非周波数ドメイン次元を持っています！"
@traitfn f(x::X) where {X; Not{HasNonFrequencyDimension{X}}} = "これは純粋な周波数ドメインスペクトルです！"
```
