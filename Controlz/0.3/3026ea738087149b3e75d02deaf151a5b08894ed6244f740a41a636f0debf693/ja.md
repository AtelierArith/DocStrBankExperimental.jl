```
o = system_order(tf::TransferFunction)
```

転送関数 `tf` の分子と分母の次数を返します。

まず、次数を決定する前に、等しい極と零をキャンセルしたい場合は [`pole_zero_cancellation`](@ref) を使用してください。

# 返り値

`o::Tuple{Int, Int}`: (分子の次数, 分母の次数)

# 例

```jldoctest
g = 1 / (s + 1)
system_order(g)
# 出力 
(0, 1)

g = (s + 1) / ((s + 2) * (s + 3))
system_order(g)
# 出力
(1, 2)
```
