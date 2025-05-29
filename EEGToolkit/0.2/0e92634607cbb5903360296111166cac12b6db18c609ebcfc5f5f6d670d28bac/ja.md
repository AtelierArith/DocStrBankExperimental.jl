`gen_time_domain(fs::Integer, s::Union{Integer, AbstractFloat}, e::Union{Integer, AbstractFloat})`

指定されたサンプリングレート $f_s$ で、秒 $s$ から秒 $e$ までの信号における時間インスタンス $t_1, \ldots, t_n$ を表す Time オブジェクトのベクターを生成します。例えば、$f_s = 500$, $s = 10, e = 11$ は $10.002, 10.004, \ldots, 10.998, 11$ にマッピングされます。

```julia
julia> gen_time_domain(500, 10, 11)
500-element Vector{Time}:
00:00:10.002
00:00:10.004
00:00:10.006
00:00:10.008
00:00:10.01
00:00:10.012
⋮
00:00:10.992
00:00:10.994
00:00:10.996
00:00:10.998
00:00:11

julia> gen_time_domain(500, 600, 6000)
2700000-element Vector{Time}:
00:10:00.002
00:10:00.004
⋮
01:39:59.998
01:40:00
```
