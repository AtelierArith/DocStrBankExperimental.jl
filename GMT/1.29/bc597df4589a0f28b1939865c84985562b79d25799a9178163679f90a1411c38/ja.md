```
earthtide(; kwargs...)
```

固体地球潮汐のグリッドまたは時系列を計算します。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`earthtide`](http://docs.generic-mapping-tools.org/latest/supplements/geodesy/earthtide.html)を参照してください。

```julia
	G = earthtide();
	imshow(G)
```
