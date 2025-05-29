```
powerT(a::T, r::S, cache1::Taylor0) where {S<:Real,T<:Number}
```

`a`を`r`の累乗にし、その結果を`cache1`に格納します。

# 引数

  * `a::T`: 基数、数値。
  * `r::S`: 指数、実数。
  * `cache1::Taylor0`: 結果を格納するキャッシュ。

# 戻り値

  * `cache1::Taylor0`: `a^r`の結果。
