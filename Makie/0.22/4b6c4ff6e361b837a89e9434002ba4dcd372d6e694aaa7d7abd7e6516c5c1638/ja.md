```
axislegend(ax, args...; position = :rt, kwargs...)
axislegend(ax, args...; position = (1, 1), kwargs...)
axislegend(ax = current_axis(); kwargs...)
axislegend(title::AbstractString; kwargs...)
axislegend(ax, title::AbstractString; kwargs...)
```

Axisのプロット領域内に配置される凡例を作成します。

位置は、最初の文字が水平方向の整列を制御し、l、r、またはcのいずれかで、2番目の文字が垂直方向の整列を制御し、t、b、またはcのいずれかであるシンボルで指定できます。また、最初の要素が凡例の水平方向の整列、2番目の要素が垂直方向の整列として設定されるタプルでも指定できます。

キーワードmergeとuniqueを使用すると、同じラベルを持つプロットオブジェクトの扱いを制御できます。mergeがtrueの場合、同じラベルを持つすべてのプロットオブジェクトは、1つの凡例エントリに重ねられます。uniqueがtrueの場合、同じプロットタイプとラベルを持つすべてのプロットオブジェクトは、1回の出現に減らされます。
