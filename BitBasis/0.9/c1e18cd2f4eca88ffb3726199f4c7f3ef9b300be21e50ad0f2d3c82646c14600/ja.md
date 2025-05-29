```
itercontrol([T=Int], nbits, positions, bit_configs)
```

ビットの制御された部分空間を反復するイテレータを返します。

# 例

`0xx10x1`を満たすすべてのビットを反復するために、ここで`x`は任意のビットを意味します。

```jldoctest
julia> for each in itercontrol(7, [1, 3, 4, 7], (1, 0, 1, 0))
           println(string(each, base=2, pad=7))
       end
0001001
0001011
0011001
0011011
0101001
0101011
0111001
0111011

```
