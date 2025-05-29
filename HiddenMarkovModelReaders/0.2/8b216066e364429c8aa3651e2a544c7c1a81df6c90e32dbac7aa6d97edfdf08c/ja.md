隠れマルコフモデルのパラメータ。

# フィールド

```
penalty::Float64: 隠れマルコフモデルのペナルティ。デフォルト = 200。
minimumFrequency::Int64: 仮説生成中に分割するモデル状態の最小頻度。デフォルト = 20。
verbosity::Bool: 冗長性を増加させる。デフォルト = false。
distance::Function: 距離を計算する。このパッケージで提供される可能なオプションには、`euclDist`、`bhattDist`が含まれます。あるいは、`functionDist(arr::Array{T, 1}, h::Array{T, 1}) where T <: Number`の形式の事前定義された関数または匿名/λ関数を渡すことができます。
```

参照: [`HMM`](@ref), [`setup`](@ref), [`euclDist`](@ref), [`bhattDist`](@ref),
