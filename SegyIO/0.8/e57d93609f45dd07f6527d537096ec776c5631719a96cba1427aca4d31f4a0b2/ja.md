```
使用法: delim_vector(x::AbstractVector, probe_length::Int)
```

`x`の各均質セクションの最初の要素のインデックスを返します。

# 例

```
julia> x = vec([1.0 1.0 1.0 2.0 2.0 2.0 2.0 3.0 3.0 3.0 3.0]);

julia> delim_vector(x, 1)
3-element Array{Int64,1}:
1
4
8
```

`probe_length`はセクションの長さの初期推測を設定します。`probe_length`をセクションの真の長さに近い値に選ぶことで、わずかなパフォーマンス向上が得られますが、単に長さを1に設定することは大きな影響はありません。

```
julia> @btime delim_vector(x,1)
  1.169 μs (3 allocations: 176 bytes)
4-element Array{Int64,1}:
      1
 100001
 100003
 200003

julia> @btime delim_vector(x,100000)
  945.615 ns (3 allocations: 176 bytes)
4-element Array{Int64,1}:
      1
 100001
 100003
 200003
```
