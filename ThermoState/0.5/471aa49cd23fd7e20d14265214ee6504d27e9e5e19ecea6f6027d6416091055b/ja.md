```
normalize_units(val)
```

通常の数値に対しては恒等関数ですが、`Unitful.Quantity`の数値やベクトルに対しては、単位を同等のSI単位に変換し、単位情報を取り除きます。

# 例

```julia-repl
julia> normalize_units(0.0u"°C")
273.15

```

```julia-repl
julia> normalize_units(273.15)
273.15
```
