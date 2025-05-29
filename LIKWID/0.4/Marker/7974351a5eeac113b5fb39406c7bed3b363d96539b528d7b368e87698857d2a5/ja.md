```
marker(f, regiontag::AbstractString)
```

指定された関数 `f` の実行の周りに LIKWID マーカー領域を追加します。内部では [`Marker.startregion`](@ref) と [`Marker.stopregion`](@ref) を使用します。`LIKWID.Marker.init()` と `LIKWID.Marker.close()` は、それぞれ前後に呼び出す必要があります。

# 例

```julia
julia> using LIKWID

julia> Marker.init()

julia> marker("sleeping...") do
           sleep(1)
       end
true

julia> marker(()->rand(100), "create rand vec")
true

julia> Marker.close()

```
