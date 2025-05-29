```
fill_nans(x, intp::Linear)
```

`x`内の`NaN`値を線形補間を使用して埋めます。`x`の左端または右端にある`NaN`は補間されず、そのまま残されます。詳細は[`fill_nans!`](@ref)を参照してください。

## 例

```julia
x = [NaN, 1.4, 5.6, NaN, 4.3, 3.1, NaN, NaN, 5.6, NaN]
fill_nans(x, Linear())
```
