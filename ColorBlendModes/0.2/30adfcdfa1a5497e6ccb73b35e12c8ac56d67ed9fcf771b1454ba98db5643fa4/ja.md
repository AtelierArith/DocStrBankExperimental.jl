```
blend(c1, c2; mode=BlendNormal, opacity=1, op=CompositeSourceOver)
```

2つの色 `c1` と `c2` の混合色を作成します。`c1` は背景色を意味し、`c2` はソース色を意味します。

`mode` はブレンドモードを指定します。例えば、[`BlendMultiply`](@ref) などです。

`opacity` はソース（すなわち `c2` 側）のアルファを乗算によって修正します。

`op` は合成操作を指定します。例えば、[`CompositeSourceAtop`](@ref) などです。

戻り値の型は `c1` と同じです。

# 例

```jldoctest
julia> blend(RGB(1, 0.5, 0), RGB(0, 0.5, 1), mode=BlendLighten)
RGB{Float64}(1.0,0.5,1.0)
```
