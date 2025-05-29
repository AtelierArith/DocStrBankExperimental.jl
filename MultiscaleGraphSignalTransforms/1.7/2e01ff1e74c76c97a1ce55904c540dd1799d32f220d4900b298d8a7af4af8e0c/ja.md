```
rngwf_lx(dic_l2x)
```

rNGWFベクトルの連続したサブインデックスを見つけます。

# 入力引数

  * `dic_l2x::Dict`: l-th 中心固有ベクトルによってQRでフィルタリングされた位置を格納する辞書

# 出力引数

  * `Γ::Vector{Tuple{Int64,Int64}}`: rNGWFベクトルの連続したサブインデックス。
