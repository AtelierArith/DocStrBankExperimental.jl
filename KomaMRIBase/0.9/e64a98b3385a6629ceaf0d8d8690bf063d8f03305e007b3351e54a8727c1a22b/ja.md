```
y = is_ADC_on(x::Sequence)
y = is_ADC_on(x::Sequence, t::Union{Array{Float64,1}, Array{Float64,2}})
```

シーケンス `seq` にADCがアクティブな要素があるか、または時間 `t` の間にアクティブであるかを示します。

# 引数

  * `x`: (`::Sequence`) シーケンス構造体
  * `t`: (`::Union{Array{Float64,1}, Array{Float64,2}}`, `[s]`) チェックする時間

# 戻り値

  * `y`: (`::Bool`) シーケンス内のADCがアクティブかどうかを示すブール値
