```
hitransform(x::Array)
```

時系列の調和逆変換を計算します。詳細については、Hassler と Hosseinkouchack (2020) を参照してください。

# 引数

  * `x::Array`: 時系列。

# 出力

  * `x::Array`: 調和逆変換後の時系列。

# 注意事項

調和逆変換は FFT を使用して計算されます。

# 例

```julia
julia> hitransform(fi_gen(100,0.2))
```
