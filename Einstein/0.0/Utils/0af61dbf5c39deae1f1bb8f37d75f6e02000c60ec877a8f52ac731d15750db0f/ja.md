```
sws_A0(s::Integer, l::Integer) where {TR<:AbstractFloat}
```

角度分離定数を $a = 0$ で計算します。

$$
{}_s A_{\ell m}(0)=l(l+1)-s(s+1)
$$

# 引数

  * `s::Integer`: スピン
  * `l::Integer`: 角度数
