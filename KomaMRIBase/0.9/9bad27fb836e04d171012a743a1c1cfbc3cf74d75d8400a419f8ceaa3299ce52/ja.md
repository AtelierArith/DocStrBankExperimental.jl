```
y = is_RF_on(x::Sequence)
y = is_RF_on(x::Sequence, t::Vector{Float64})
```

シーケンス `seq` に RF がアクティブな要素があるか、または時間 `t` の間にアクティブであるかを示します。

# 引数

  * `x`: (`::Sequence`) シーケンス構造体
  * `t`: (`::Vector{Float64}`, `[s]`) チェックする時間

# 戻り値

  * `y`: (`::Bool`) シーケンス内の RF がアクティブかどうかを示すブール値
