```
interpolate(m::HealpixMap{T, RingOrder, AA}, θ, ϕ) -> 値
interpolate(m::HealpixMap{T, RingOrder, AA}, θ, ϕ, pixbuf, weightbuf) -> 値
```

指定された方向に沿ったマップの補間値を返します。

提供される場合、パラメータ `pixbuf` と `weightbuf` は、それぞれ整数と浮動小数点値の4要素の配列でなければなりません。これらは、ヒープの割り当てを節約するために、`interpolate` の複数の呼び出しで再利用できます。また、内部で使用されるため、初期化する必要はありません：

```
pixbuf = Array{Int}(undef, 4)
weightbuf = Array{Float64}(undef, 4)

m = HealpixMap{Float64, RingOrder}(1)
for (θ, ϕ) in [(0., 0.), (π/2, π/2)]
    println(interpolate(m, θ, ϕ, pixbuf, weightbuf))
end
```

`pixbuf` と `weightbuf` を渡すことで、時間を節約できます。この単純なベンチマークが示しています：

```
julia> @benchmark interpolate(m, rand(), rand(), pixbuf, weightbuf)
BenchmarkTools.Trial:
  memory estimate:  618 bytes
  allocs estimate:  9
  --------------
  minimum time:     283.184 ns (0.00% GC)
  median time:      296.140 ns (0.00% GC)
  mean time:        348.132 ns (9.55% GC)
  maximum time:     10.627 μs (95.88% GC)
  --------------
  samples:          10000
  evals/sample:     282

julia> @benchmark interpolate(m, rand(), rand())
BenchmarkTools.Trial:
  memory estimate:  837 bytes
  allocs estimate:  11
  --------------
  minimum time:     329.825 ns (0.00% GC)
  median time:      345.504 ns (0.00% GC)
  mean time:        417.004 ns (11.04% GC)
  maximum time:     13.733 μs (96.21% GC)
  --------------
  samples:          10000
  evals/sample:     223
```
