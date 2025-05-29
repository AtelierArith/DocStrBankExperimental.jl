```
axislegend(ax, args...; position = :rt, kwargs...)
axislegend(ax, args...; position = (1, 1), kwargs...)
axislegend(ax = current_axis(); kwargs...)
axislegend(title::AbstractString; kwargs...)
```

軸のプロット領域内に配置される凡例を作成します。

位置はシンボルで、最初の文字が水平方向の配置を制御し、l、r、またはcのいずれかになります。2番目の文字は垂直方向の配置を制御し、t、b、またはcのいずれかになります。また、最初の要素が凡例の水平方向の配置、2番目の要素が垂直方向の配置として設定されるタプルでも構いません。

キーワードmergeとuniqueを使用すると、同じラベルを持つプロットオブジェクトの扱いを制御できます。mergeがtrueの場合、同じラベルを持つすべてのプロットオブジェクトは、1つの凡例エントリに重ねられます。uniqueがtrueの場合、同じプロットタイプとラベルを持つすべてのプロットオブジェクトは1回の出現に減らされます。
