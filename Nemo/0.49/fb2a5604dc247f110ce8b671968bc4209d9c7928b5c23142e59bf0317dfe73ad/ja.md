```
setbit!(x::ZZRingElem, c::Int)
```

$$
x
$$

の$c$ビットを設定します。最下位ビットは$0$-thビットです。この関数は入力をインプレースで変更することに注意してください。

# 例

```jldoctest
julia> a = ZZ(12)
12

julia> setbit!(a, 0)

julia> a
13
```
