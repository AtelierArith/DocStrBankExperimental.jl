```
normalize_n(s, n; <キーワード引数>)
```

[0, n]の範囲に正規化します。デフォルトは[0, +1]です。

# 引数

  * `s::AbstractArray`
  * `n::Real=1.0`
  * `bych::Bool=false`: trueの場合、各チャネルを別々に正規化します

# 戻り値

  * `sn::AbstractArray`
