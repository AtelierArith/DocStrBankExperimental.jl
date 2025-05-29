レンコチャートパターン

# メソッド

```
function renko(x::Array{T}; box_size::T=10.0)::Array{Int} where {T<:Real}

function renko(hlc::Matrix{T}; box_size::T=10.0, use_atr::Bool=false, n::Int=14)::Array{Int} where {T<:Real}
```

  * 従来型（定数ボックスサイズ）： `renko(x::Array{T}; box_size::T=10.0)::Array{Int}`
  * ATR動的ボックスサイズ： `renko(hlc::Matrix{T}; box_size::T=10.0, use_atr::Bool=false, n::Int=14)::Array{Int}`

# 出力

`Array{Int}`オブジェクトのサイズはNx1（ここでNは`x`の行数）で、各要素は`x`の対応する行のレンコバー番号を示します。
