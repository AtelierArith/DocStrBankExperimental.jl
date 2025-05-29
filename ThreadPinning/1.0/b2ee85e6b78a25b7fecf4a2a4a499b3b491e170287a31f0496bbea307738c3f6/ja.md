```
with_pinthreads(f::F, args...;
    soft = false,
    kwargs...
)
```

指定されたピン留めで関数 `f` を実行し、その後に以前のスレッドアフィニティを復元します。通常は do 構文と組み合わせて使用されます。

デフォルトでは（`soft=false`）、スレッドアフィニティが復元される前に、Julia スレッドは以前に実行されていた CPU スレッドにピン留めされます。

**例**

```julia
julia> getcpuids()
4-element Vector{Int64}:
  7
 75
 63
  4

julia> with_pinthreads(:cores) do
           getcpuids()
       end
4-element Vector{Int64}:
 0
 1
 2
 3

julia> getcpuids()
4-element Vector{Int64}:
  7
 75
 63
  4
```
