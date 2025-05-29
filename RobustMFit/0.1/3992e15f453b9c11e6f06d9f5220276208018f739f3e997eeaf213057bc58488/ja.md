```
Hampel(kL::Vector{Real}, kU::Vector{Real}) <: HampelSetting
Hampel(k::Vector{Real}) <: HampelSetting
```

Hampelの関数を使用したM推定における関数選択のためのデータ型。`kL`と`kU`はそれぞれ下限および上限の調整定数（ベクトル）を提供します。調整定数ベクトルが1つだけ提供された場合、対称関数が仮定されます。

# 例

```julia
Hampel([1, 2, 5], [1, 4, 7])
Hampel([1, 2, 5])
```
