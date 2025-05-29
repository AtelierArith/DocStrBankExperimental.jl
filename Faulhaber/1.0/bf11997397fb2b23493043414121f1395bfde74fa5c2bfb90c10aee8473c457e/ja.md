```
faulhaber(m, ::Val{p})
```

$$
O(p)
$$

時間で `sum(i->i^p, 1:m)` の合計を計算します。`m` が整数の場合、この関数は整数オーバーフローが発生しないと仮定して、正確な整数解を返します。`m` が浮動小数点数の場合、あまり正確でない浮動小数点解を返します。

例:

```julia
julia> using BenchmarkTools, Faulhaber

julia> @btime faulhaber(Ref(Int128(2000))[], Val(7))
  1.143 ns (0 allocations: 0 bytes)
32064037333328666667000000

julia> @btime sum(i->i^7, 1:Int128(2000))
  12.282 μs (0 allocations: 0 bytes)
32064037333328666667000000

julia> @btime faulhaber(Ref(2000.0)[], Val(7))
  1.134 ns (0 allocations: 0 bytes)
3.2064037333328662e25
```
