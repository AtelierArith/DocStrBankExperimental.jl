```
u1_val = si_units(u1)
meter = si_units(:meter)
meter, hour = si_units(:meter, :hour)
```

複数の単位を同時に変換するためのSI単位の乗法変換係数を取得します。返される値は、各入力引数に対して1つの値を持つ`Tuple`です。各入力引数は、`String`または`Symbol`のいずれかです。

# 例

```jldoctest
julia> meter, hour = si_units(:meter, :hour)
(1.0, 3600.0)
```
