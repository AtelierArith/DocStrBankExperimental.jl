```
cplxpair(x)
```

実数値でソートし、次に複素共役ペアでソートするために使用されます。より正の実数が最初に来て、次に虚部が小さいペアが続きます。

# 例

```julia
real_values = [-1, -3, -2]
complex_values = [-1 + 1im, -2 - 2im, -1 + 2im]
sorted_values = sort!([complex_values; conj(complex_values); real_values], by = cplxpair)

# 出力

9-element Vector{Complex{Int64}}:
 -1 + 0im
 -2 + 0im
 -3 + 0im
 -1 - 1im
 -1 + 1im
 -1 - 2im
 -1 + 2im
 -2 - 2im
 -2 + 2im
```
