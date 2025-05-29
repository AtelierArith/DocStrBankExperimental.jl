```
function unicode_scalarplot(
	u::FEVectorBlock; 
	components = 1:get_ncomponents(u),
	abs = false,
	resolution = (30,30),
	colormap = :viridis,
	title = u.name,
	kwargs...)
```

(UnicodePlotsを必要とする拡張を介して)

FEVectorBlock uの有限要素関数の成分を、粗い均一メッシュにlazy_interpolate!を使用してプロットし、1Dまたは2Dの場合はそれぞれUnicodePlots.jlのlineplotまたはheatmapを使用します。

1Dではすべての成分が同じlineplotにプロットされ、2Dではすべての成分が別々のheatmapにプロットされます。

abs = trueの場合、成分の絶対値のみがプロットされます。
