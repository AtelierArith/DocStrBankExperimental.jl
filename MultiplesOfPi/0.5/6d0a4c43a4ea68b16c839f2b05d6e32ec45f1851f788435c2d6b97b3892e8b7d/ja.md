```
π
```

数値的に `pi` と等価な `PiExpTimes(1, 1)`。`pi` の代わりに `Pi` を使用することで、浮動小数点の不正確さを回避する結果が得られることがよくあります。

# 例

```jldoctest
julia> sin(2Pi) == 0
true

julia> sin(2π) == 0
false

julia> exp(im*Pi) + 1 == 0
true

julia> exp(im*π) + 1 == 0
false

julia> (2//3)Pi + Pi == (5//3)Pi
true

julia> (2//3)π + π == (5//3)π
false
```
