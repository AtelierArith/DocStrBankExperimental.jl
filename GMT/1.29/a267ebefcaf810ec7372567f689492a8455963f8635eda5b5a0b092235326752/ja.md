I = mosaic(; region=??, ...)

上記と同様ですが、今回は `region` オプションから BoundingBox が抽出されます。このオプションは、例えば `coast` モジュールと同じです。

# 例

```jldoctest
julia> I = mosaic(region=(91,110,6,22))		# ズームレベルは自動的に計算されます
viz(I, coast=true)
```
