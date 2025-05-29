```
get_destination_bit(readout::Readout)::Int
```

`readout`の結果が送られる古典ビットのインデックスを返します。

# 例

```jldoctest
julia> get_destination_bit(readout(2, 3))
3

```
